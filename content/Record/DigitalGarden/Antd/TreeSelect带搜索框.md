---
UID: 20230514114911 
title: "TreeSelect带搜索框"
tags: 
aliases: 
source: 
cssclass: 
created: 2023-05-14
Update: NaN
---

## ✍内容


```jsx
import { Button, Input, Radio, TreeSelect } from "antd";  
import React, { useEffect, useState } from "react";  
import { FolderOutlined ,DownOutlined} from "@ant-design/icons";  
import styles from "../theme/SNSelectTree.module.scss";  
function SNTreeSelect(props) {  
// 搜索框值  
const [searchValue, setSearchValue] = useState(""); // 搜索框值  
//树形选择器  
const [tree, setTree] = useState();  
//树形选择器数据  
const treeData = [  
{  
title: "南国药业",  
value: "南国药业",  
  
children: [  
{  
title: "司南科技",  
value: "司南科技",  
},  
{  
title: "著忙科技",  
value: "著忙科技",  
},  
],  
},  
{  
title: "重负信息",  
value: "重负信息",  
children: [],  
},  
];  
//树形选择器事件  
useEffect(() => {  
setTree(props.treeValue);  
}, [props]);  
const treeChangeHandler = (newValue) => {  
if (props.handleTreeData) {  
props.handleTreeData({ ...props.identify, post: newValue });  
}  
if (props.treeSelect) {  
props.treeSelect(newValue);  
}  
setTree(newValue);  
};  
// 搜索框的值发生改变searchValue值也跟着改变  
const handleChangeSearch = (e) => {  
setSearchValue(e.target.value || "");  
};  
  
// 下拉数据二级处理  
const formatChildTreeData = (data, result) => {  
data.forEach((cur) => {  
if (cur.title.includes(searchValue)) {  
result.push(cur);  
} else if (cur.children && cur.children.length) {  
const childResult = formatChildTreeData(cur.children, result);  
if (childResult.length) {  
result.push({  
...cur,  
children: childResult,  
});  
}  
}  
});  
return result;  
};  
// 处理下拉框数据  
const formatTreeData = () => {  
// 当搜索框没有值的时候不做处理  
if (!searchValue) return treeData;  
const result = [];  
treeData.forEach((item) => {  
if (item.title.includes(searchValue)) {  
result.push(item);  
} else if (item.children && item.children.length) {  
const childResult = formatChildTreeData(item.children, []);  
if (childResult.length) {  
result.push({  
...item,  
children: childResult,  
});  
}  
}  
});  
return result;  
};  
  
  
function renderTreeNodes(data) {  
return data.map((item) => {  
if (item.children) {  
item.icon = <FolderOutlined />;  
return (  
<TreeSelect.TreeNode  
key={item.key}  
title={<div>123</div>}  
>  
{renderTreeNodes(item.children)}  
</TreeSelect.TreeNode>  
);  
} else {  
let test  
if(tree)  
{  
test=tree.value===item.value  
}  
item.title = <Radio checked={test}>{item.title}</Radio>;  
  
  
}  
return (  
<TreeSelect.TreeNode key={item.key} title={item.title.props.children} />  
);  
});  
}  
  
const renderTitle=(value)=>{  
console.log(123,value);  
}  
  
return (  
<div>  
<TreeSelect  
style={{  
width: "100%",  
}}  
  
labelInValue  
className={styles.tree}  
bordered={props.border}  
treeNodeFilterProp="title"  
treeIcon={true}  
fieldNames={{  
title:456  
}}  
value={tree}  
dropdownStyle={{  
maxHeight: 400,  
overflow: "auto",  
}}  
onDropdownVisibleChange={() => setSearchValue("")} // 展开下拉菜单的回调  
dropdownRender={(menu) => (  
<>  
<Input  
style={{  
width: "300",  
borderBottom: "1px solid #d9d9d9",  
marginBottom: "10px",  
}}  
suffix="RMB"  
onChange={handleChangeSearch}  
value={searchValue}  
placeholder="请搜索"  
allowClear={true}  
bordered={false}  
/>  
{menu}  
</>  
)} // 自定义下拉框内容  
allowClear={true}  
showSearch  
suffixIcon={<FolderOutlined />}//搜索按钮  
treeData={formatTreeData()}  
treeDefaultExpandAll  
onChange={treeChangeHandler}  
>  
{renderTreeNodes(treeData)}  
</TreeSelect>  
</div>  
);  
}  
export default React.memo(SNTreeSelect);
```