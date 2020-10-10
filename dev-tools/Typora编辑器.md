## 调整编辑器文字区域宽度，默认太窄了
打开开发者模式，查看样式发现默认宽度为40em。打开偏好设置->外观->打开主题文件夹->newsprint.css(我用的newsprint主题)，修改样式
```css
#write {
	max-width: 80em;
}
```
