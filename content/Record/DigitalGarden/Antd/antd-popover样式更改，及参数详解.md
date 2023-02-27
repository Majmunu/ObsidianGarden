

---
title: "antd-popover样式更改，及参数详解"
tags:
- Antd
---
---


 

```html
<Popover
     overlayClassName={ styles.ant_popover }//样式类
     title={111}//标题
     content={222}//内容
     trigger='click'//触发方式-hover-focus
     visible={show}//手动显示
     placement="topLeft"//相对页面内容，popover位置变化-共有12种方向
     onVisibleChange={this.datePageChange}//popover焦点变化-聚焦-失焦
 >
     <Button>click</Button>//页面内容
 </Popover>
```   

```css
.pop{
    :global{
        .ant-popover-inner{
            background-color: #2D3B5A;
        }
        .ant-popover-arrow-content {

            --antd-arrow-background-color: #171F29!important;

        }
        .ant-popover-placement-top > .ant-popover-content > .ant-popover-arrow, .ant-popover-placement-topLeft > .ant-popover-content > .ant-popover-arrow, .ant-popover-placement-topRight > .ant-popover-content > .ant-popover-arrow{
            border-right-color: #2d3b5a;
            border-bottom-color: #2d3b5a;
            background: #2d3b5a;
        }
    } 
}
```
