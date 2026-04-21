# 形色字构质动 — 完整提取指南

使用 `agent-browser` 精确提取网站的六大设计维度。

## 快速启动检查清单

```
□ agent-browser 已安装且可用
□ 目标 URL 可访问
□ 准备执行 JavaScript 提取代码
□ 准备模拟不同视口尺寸
□ 准备测试交互状态
```

## 一、色 (Color) — 完整色彩系统

### 1.1 基础颜色提取脚本

```javascript
// 执行在 agent-browser eval 中
function extractColors() {
  const colors = {
    text: new Set(),
    background: new Set(),
    border: new Set(),
    accent: new Set()
  };
  
  document.querySelectorAll('*').forEach(el => {
    const styles = getComputedStyle(el);
    colors.text.add(styles.color);
    colors.background.add(styles.backgroundColor);
    colors.border.add(styles.borderColor);
  });
  
  return {
    text: [...colors.text].slice(0, 20),
    background: [...colors.background].slice(0, 20),
    border: [...colors.border].slice(0, 20)
  };
}

extractColors();
```

### 1.2 CSS 变量颜色提取

```javascript
function extractCSSColorVars() {
  const root = getComputedStyle(document.documentElement);
  const colors = {};
  
  for (let prop of root) {
    if (prop.includes('color') || prop.includes('bg') || prop.includes('brand')) {
      const value = root.getPropertyValue(prop).trim();
      if (value && value.match(/^(#|rgb|hsl)/)) {
        colors[prop] = value;
      }
    }
  }
  
  return colors;
}

extractCSSColorVars();
```

### 1.3 语义色识别

```javascript
function identifySemanticColors() {
  // 查找按钮、警告、成功提示等元素
  const semantic = {
    primary: [],
    success: [],
    warning: [],
    error: [],
    info: []
  };
  
  // 主按钮颜色
  document.querySelectorAll('.btn-primary, .button-primary, [class*="primary"]').forEach(el => {
    semantic.primary.push(getComputedStyle(el).backgroundColor);
  });
  
  // 成功色
  document.querySelectorAll('.success, .btn-success, [class*="success"]').forEach(el => {
    semantic.success.push(getComputedStyle(el).backgroundColor || getComputedStyle(el).color);
  });
  
  return semantic;
}

identifySemanticColors();
```

## 二、形 (Form) — 形状语言系统

### 2.1 圆角系统提取

```javascript
function extractBorderRadius() {
  const radii = new Set();
  const radiusMap = {};
  
  document.querySelectorAll('button, .card, input, .badge, img').forEach(el => {
    const r = getComputedStyle(el).borderRadius;
    radii.add(r);
    
    // 分类
    if (el.tagName === 'BUTTON') radiusMap.button = r;
    if (el.classList.contains('card')) radiusMap.card = r;
    if (el.tagName === 'INPUT') radiusMap.input = r;
  });
  
  return {
    all: [...radii],
    byComponent: radiusMap
  };
}

extractBorderRadius();
```

### 2.2 阴影层级提取

```javascript
function extractShadows() {
  const shadows = {
    none: [],
    sm: [],
    md: [],
    lg: [],
    xl: []
  };
  
  document.querySelectorAll('.card, .modal, .popover, .dropdown, button:hover').forEach(el => {
    const shadow = getComputedStyle(el).boxShadow;
    if (shadow && shadow !== 'none') {
      // 根据模糊半径分类
      const blurMatch = shadow.match(/(\d+)px/);
      if (blurMatch) {
        const blur = parseInt(blurMatch[1]);
        if (blur < 4) shadows.sm.push(shadow);
        else if (blur < 8) shadows.md.push(shadow);
        else if (blur < 16) shadows.lg.push(shadow);
        else shadows.xl.push(shadow);
      }
    }
  });
  
  return shadows;
}

extractShadows();
```

## 三、字 (Typography) — 字体系统

### 3.1 完整字体层级提取

```javascript
function extractTypographyScale() {
  const scale = {
    display: [],
    heading: [],
    body: [],
    ui: []
  };
  
  const selectors = [
    { sel: 'h1', type: 'heading', level: 1 },
    { sel: 'h2', type: 'heading', level: 2 },
    { sel: 'h3', type: 'heading', level: 3 },
    { sel: 'h4', type: 'heading', level: 4 },
    { sel: '.display, .hero-title, [class*="display"]', type: 'display' },
    { sel: 'p, .body', type: 'body' },
    { sel: '.small, .caption, .meta', type: 'ui' },
    { sel: 'button, .btn, nav a', type: 'ui' }
  ];
  
  selectors.forEach(({ sel, type }) => {
    document.querySelectorAll(sel).forEach(el => {
      const styles = getComputedStyle(el);
      scale[type].push({
        selector: sel,
        fontFamily: styles.fontFamily,
        fontSize: styles.fontSize,
        fontWeight: styles.fontWeight,
        lineHeight: styles.lineHeight,
        letterSpacing: styles.letterSpacing,
        textTransform: styles.textTransform
      });
    });
  });
  
  return scale;
}

extractTypographyScale();
```

### 3.2 字体族提取

```javascript
function extractFontFamilies() {
  const families = new Set();
  
  document.querySelectorAll('*').forEach(el => {
    families.add(getComputedStyle(el).fontFamily);
  });
  
  return [...families].filter(f => f && f !== 'inherit');
}

extractFontFamilies();
```

## 四、构 (Structure) — 布局与间距

### 4.1 间距系统分析

```javascript
function extractSpacingSystem() {
  const spacings = new Set();
  const baseUnit = 4; // 常见 base unit
  
  document.querySelectorAll('*').forEach(el => {
    const styles = getComputedStyle(el);
    const values = [
      styles.padding,
      styles.margin,
      styles.gap,
      styles.gridGap,
      styles.rowGap,
      styles.columnGap
    ];
    
    values.forEach(v => {
      if (v && v !== '0px') {
        spacings.add(v);
      }
    });
  });
  
  // 识别可能的 spacing scale
  const numericSpacings = [...spacings].map(s => {
    const match = s.match(/(\d+)px/);
    return match ? parseInt(match[1]) : null;
  }).filter(Boolean);
  
  // 找规律（是否是 4 或 8 的倍数）
  const base4 = numericSpacings.filter(n => n % 4 === 0);
  const base8 = numericSpacings.filter(n => n % 8 === 0);
  
  return {
    allSpacings: [...spacings],
    baseUnitGuess: base8.length > base4.length ? 8 : 4,
    uniqueValues: [...new Set(numericSpacings)].sort((a, b) => a - b)
  };
}

extractSpacingSystem();
```

### 4.2 网格系统提取

```javascript
function extractGridSystem() {
  const grids = [];
  
  document.querySelectorAll('[class*="grid"], [style*="grid"], section, .container').forEach(el => {
    const styles = getComputedStyle(el);
    if (styles.display === 'grid' || styles.display === 'flex') {
      grids.push({
        element: el.tagName + (el.className ? '.' + el.className.split(' ')[0] : ''),
        display: styles.display,
        gridTemplateColumns: styles.gridTemplateColumns,
        gap: styles.gap,
        maxWidth: styles.maxWidth,
        padding: styles.padding
      });
    }
  });
  
  return grids.slice(0, 10); // 取前10个
}

extractGridSystem();
```

### 4.3 容器宽度提取

```javascript
function extractContainerWidths() {
  const widths = new Set();
  
  document.querySelectorAll('.container, .wrapper, section, main, [class*="container"]').forEach(el => {
    const w = getComputedStyle(el).maxWidth;
    if (w && w !== 'none') widths.add(w);
  });
  
  return [...widths];
}

extractContainerWidths();
```

## 五、质 (Quality) — 质感与材质

### 5.1 渐变提取

```javascript
function extractGradients() {
  const gradients = new Set();
  
  document.querySelectorAll('*').forEach(el => {
    const bg = getComputedStyle(el).background;
    if (bg && bg.includes('gradient')) {
      gradients.add(bg);
    }
  });
  
  return [...gradients].slice(0, 10);
}

extractGradients();
```

### 5.2 特殊效果检测

```javascript
function extractSpecialEffects() {
  const effects = {
    blur: [],
    opacity: [],
    texture: []
  };
  
  document.querySelectorAll('*').forEach(el => {
    const styles = getComputedStyle(el);
    
    // 毛玻璃效果
    if (styles.backdropFilter && styles.backdropFilter !== 'none') {
      effects.blur.push({
        element: el.className || el.tagName,
        backdropFilter: styles.backdropFilter
      });
    }
    
    // 半透明
    if (styles.opacity && styles.opacity !== '1') {
      effects.opacity.push({
        element: el.className || el.tagName,
        opacity: styles.opacity
      });
    }
  });
  
  return effects;
}

extractSpecialEffects();
```

## 六、动 (Motion) — 动效系统

### 6.1 过渡效果提取

```javascript
function extractTransitions() {
  const transitions = new Set();
  
  document.querySelectorAll('button, a, .card, input, [class*="hover"]').forEach(el => {
    const t = getComputedStyle(el).transition;
    if (t && t !== 'all 0s ease 0s') {
      transitions.add(t);
    }
  });
  
  return [...transitions].slice(0, 15);
}

extractTransitions();
```

### 6.2 动画关键帧提取

```javascript
function extractAnimations() {
  const animations = new Set();
  
  document.querySelectorAll('*').forEach(el => {
    const a = getComputedStyle(el).animation;
    if (a && a !== 'none 0s ease 0s 1 normal none running') {
      animations.add(a);
    }
  });
  
  // 获取关键帧定义
  const sheets = [...document.styleSheets];
  const keyframes = [];
  
  sheets.forEach(sheet => {
    try {
      [...sheet.cssRules].forEach(rule => {
        if (rule.type === CSSRule.KEYFRAMES_RULE) {
          keyframes.push({
            name: rule.name,
            cssText: rule.cssText
          });
        }
      });
    } catch (e) {
      // 跨域样式表无法访问
    }
  });
  
  return {
    usedAnimations: [...animations],
    keyframeDefinitions: keyframes.slice(0, 10)
  };
}

extractAnimations();
```

### 6.3 交互状态变化检测

```javascript
// 测试 Hover 状态
async function testHoverStates() {
  const interactiveElements = document.querySelectorAll('button, a, .btn, .card');
  const hoverEffects = [];
  
  for (let el of interactiveElements.slice(0, 5)) {
    const before = {
      background: getComputedStyle(el).backgroundColor,
      color: getComputedStyle(el).color,
      transform: getComputedStyle(el).transform,
      boxShadow: getComputedStyle(el).boxShadow
    };
    
    // 模拟 hover
    el.dispatchEvent(new MouseEvent('mouseenter', { bubbles: true }));
    await new Promise(r => setTimeout(r, 100));
    
    const after = {
      background: getComputedStyle(el).backgroundColor,
      color: getComputedStyle(el).color,
      transform: getComputedStyle(el).transform,
      boxShadow: getComputedStyle(el).boxShadow
    };
    
    // 恢复
    el.dispatchEvent(new MouseEvent('mouseleave', { bubbles: true }));
    
    hoverEffects.push({
      element: el.tagName + (el.className ? '.' + el.className.split(' ')[0] : ''),
      before,
      after,
      changed: JSON.stringify(before) !== JSON.stringify(after)
    });
  }
  
  return hoverEffects;
}

testHoverStates();
```

## 七、响应式断点测试

### 7.1 自动断点检测

```javascript
async function testResponsiveBreakpoints() {
  const breakpoints = [375, 768, 1024, 1440, 1920];
  const results = {};
  
  for (let bp of breakpoints) {
    // 调整视口
    window.innerWidth = bp;
    window.dispatchEvent(new Event('resize'));
    await new Promise(r => setTimeout(r, 300));
    
    // 记录布局变化
    results[bp] = {
      container: document.querySelector('.container, section')?.offsetWidth,
      gridColumns: getComputedStyle(document.querySelector('[class*="grid"]') || document.body).gridTemplateColumns,
      fontSize: getComputedStyle(document.querySelector('h1') || document.body).fontSize
    };
  }
  
  return results;
}

testResponsiveBreakpoints();
```

## 八、综合提取脚本

一键提取所有核心设计 token：

```javascript
function extractCompleteDesignSystem() {
  return {
    // 色
    colors: extractColors(),
    cssColorVars: extractCSSColorVars(),
    semanticColors: identifySemanticColors(),
    gradients: extractGradients(),
    
    // 形
    borderRadius: extractBorderRadius(),
    shadows: extractShadows(),
    
    // 字
    typography: extractTypographyScale(),
    fonts: extractFontFamilies(),
    
    // 构
    spacing: extractSpacingSystem(),
    grid: extractGridSystem(),
    containers: extractContainerWidths(),
    
    // 质
    effects: extractSpecialEffects(),
    
    // 动
    transitions: extractTransitions(),
    animations: extractAnimations(),
    
    // 元数据
    url: window.location.href,
    timestamp: new Date().toISOString(),
    viewport: {
      width: window.innerWidth,
      height: window.innerHeight
    }
  };
}

// 执行
extractCompleteDesignSystem();
```

## 九、常见网站特定提取

### 9.1 React/Next.js 网站

```javascript
// React 组件特定类名
const reactSelectors = {
  buttons: '[class*="Button"], [class*="btn"], button[class*="Mui"]',
  cards: '[class*="Card"], [class*="card"], .MuiCard-root',
  inputs: '[class*="Input"], [class*="TextField"], input[class*="Mui"]'
};

Object.entries(reactSelectors).forEach(([type, selector]) => {
  console.log(type, document.querySelectorAll(selector).length);
});
```

### 9.2 Tailwind 网站

```javascript
// 识别 Tailwind 类
const tailwindClasses = new Set();
document.querySelectorAll('*').forEach(el => {
  el.classList.forEach(c => {
    if (c.match(/^(bg-|text-|p-|m-|w-|h-|flex|grid|rounded|shadow)/)) {
      tailwindClasses.add(c);
    }
  });
});

// 分析 Tailwind 配置模式
const tailwindConfig = {
  colors: [...tailwindClasses].filter(c => c.startsWith('bg-') || c.startsWith('text-')),
  spacing: [...tailwindClasses].filter(c => c.match(/^(p|m)(t|r|b|l|x|y)?-/)),
  layout: [...tailwindClasses].filter(c => c.match(/^(flex|grid|col|row)/))
};

tailwindConfig;
```

## 十、提取后处理

### 去重和标准化

```javascript
// 颜色标准化为 hex
function standardizeColor(color) {
  const div = document.createElement('div');
  div.style.color = color;
  document.body.appendChild(div);
  const computed = getComputedStyle(div).color;
  document.body.removeChild(div);
  
  // rgb(r, g, b) -> #RRGGBB
  const match = computed.match(/rgb\((\d+),\s*(\d+),\s*(\d+)\)/);
  if (match) {
    const hex = [match[1], match[2], match[3]]
      .map(n => parseInt(n).toString(16).padStart(2, '0'))
      .join('');
    return '#' + hex;
  }
  return color;
}

// 像素值提取
function extractPx(value) {
  const match = value.match(/(\d+(?:\.\d+)?)px/);
  return match ? parseFloat(match[1]) : null;
}
```

### 生成间距 scale

```javascript
function generateSpacingScale(values) {
  const pxValues = values.map(extractPx).filter(Boolean);
  const unique = [...new Set(pxValues)].sort((a, b) => a - b);
  
  // 识别 base unit
  const gcd = (a, b) => b ? gcd(b, a % b) : a;
  const baseUnit = unique.reduce((acc, val) => gcd(acc, val), unique[0]);
  
  // 生成 scale
  const scale = {};
  unique.forEach((val, i) => {
    const multiplier = Math.round(val / baseUnit);
    scale[multiplier] = `${val}px`;
  });
  
  return { baseUnit, scale };
}
```

## 十一、质量保证检查表

提取完成后，对照此表验证完整性：

```
□ 色 (Color)
  □ 至少提取到主色 + 3 个辅助色
  □ 中性色阶（灰度）完整
  □ CSS 变量中的颜色值
  □ 渐变定义（如有）

□ 形 (Form)
  □ 圆角值（至少 3 个级别）
  □ 阴影层级（至少 2 个级别）
  □ 边框样式定义

□ 字 (Typography)
  □ 字体族名称（包括 fallbacks）
  □ 至少 5 级字号
  □ 字重使用记录
  □ 行高比例

□ 构 (Structure)
  □ 间距系统（base unit 识别）
  □ 网格定义
  □ 容器最大宽度
  □ 响应式断点

□ 质 (Quality)
  □ 渐变定义
  □ 特殊效果（毛玻璃等）
  □ 透明度使用

□ 动 (Motion)
  □ 过渡时长
  □ 缓动函数
  □ 动画关键帧（如有）
  □ Hover 状态变化
```

## 十二、故障排除

### 问题：提取的颜色太多/混乱
**解决**：聚焦于特定元素类型，如按钮、链接、标题。

### 问题：CSS 变量获取为空
**解决**：使用 `getComputedStyle(document.documentElement)` 并遍历所有属性。

### 问题：响应式样式无法获取
**解决**：实际调整视口尺寸并重新计算样式。

### 问题：动画 timing 不准确
**解决**：查看 `animation-duration` 和 `animation-timing-function`。

---

**记住**：完美的提取需要多次迭代。先用脚本批量获取，再针对性地深入特定元素。
