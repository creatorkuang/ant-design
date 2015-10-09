# 配置

- order: 2

配置选择框的默认属性。

---

````jsx
var Table = antd.Table;
var columns = [{
  title: '姓名',
  dataIndex: 'name',
  render: function(text) {
    return <a href="javascript:;">{text}</a>;
  }
}, {
  title: '年龄',
  dataIndex: 'age'
}, {
  title: '住址',
  dataIndex: 'address'
}];
var data = [{
  key: '1',
  name: '胡彦斌',
  age: 32,
  address: '西湖区湖底公园1号'
}, {
  key: '2',
  name: '胡彦祖',
  age: 42,
  address: '西湖区湖底公园1号'
}, {
  key: '3',
  name: '李大嘴',
  age: 32,
  address: '西湖区湖底公园1号'
}];

// 通过 rowSelection 对象表明需要行选择
var rowSelection = {
  getCheckboxProps: function (value) {
    return {
      defaultValue: value.name === '李大嘴', // 配置默认勾选的列
      disabled: value.name === '胡彦祖'    // 配置无法勾选的列
    }
  },
  onSelect: function(record, selected, selectedRows) {
    console.log(record, selected, selectedRows);
  },
  onSelectAll: function(selected, selectedRows) {
    console.log(selected, selectedRows);
  }
};

React.render(<Table rowSelection={rowSelection} columns={columns} dataSource={data} />
, document.getElementById('components-table-demo-row-selection-props'));
````