# 软工三:情报搜集系统

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

# 软工三大作业日志：前端

访问令牌:glpat-wyhQ-mCypUqj8vHM14mo


**2024/3/4**

本次作业页面:
- 主页面:包含数据项的展示,搜索,筛选,分页以及数据的增删改查(star)
- 详细信息页面:实现数据的详细展示,修改,删除,以及数据的增删改查(star)
- 个人信息节目 ?
- 登录界面 ? 考虑要不要

**todo**:
- 精简,修改侧边栏 check
- 删除多余的页面  
- 登录功能 ? 待定
- 主页面:
  - 完成筛选功能
  - 完成搜索功能 check
  - 完成分页功能 check
  - 表上方加入属性搜索框 待定
  - 完成数据的增删改查函数
- 详细信息页面:
  - 完成数据的详细展示
  - 完成数据的修改
  - 修改后的提交
  - 跳转时组件的传值:页面为空或者是获取某个数据,分别对应添加和修改
- axios的使用,封装请求函数,统一处理错误,统一处理返回数据,其中拦截待定

## 日志
**目前的主页面为home页,地址为views/home**
- 3.5
完成了模板的重新选择和项目结构的梳理,在导航栏加入了自己的项目,页面中主要完成了筛选按钮:点击后弹出筛选窗口,以及搜索栏:自动补全.现在在做将script>迁移到setup但是由于版本问题未完成

- 3.6
完善了筛选框,加入了多选框,下拉选择等,先打个样,等后续给出筛选选项再修改.另外加入了一个表的模板.

- 3.7
修改了侧边栏,修改了默认路径.重新设计了表格样式,加入了分页功能,同时点击各属性可以排序.各行可以点击查看详细属性.另外修复了图标无法显示的bug,加入了模板的图标库,

- 3.11
加入了mock来模拟API的获取,修改了表格项目,加入了搜索功能,表项加入多选框
todo:修改删除按钮样式,使得选择不为空时可以点击(check),再增加一个confirm框.另外加入图片点击的放大显示
创造了detail页面与页面的跳转

- 3.12
完成了删除选中项

- 3.13
完成了addNews页面的大致形态

- 3.14 
完成了editNews页面，但是需要home.vue传递参数，如下：
```js
// home.vue
  async handleEditNews(id) {
    try {
      const response = await this.$axios.get(`/api/news/${id}`); // 假设后端接口路径为/api/news/:id
      const newsData = response.data; // 获取后端返回的新闻数据
      this.$router.push({ name: 'editNews', params: { newsData } }); // 跳转到 editNews.vue 并传递新闻数据
    } catch (error) {
      console.error('获取新闻数据失败', error);
    }
  }
```
```js
// editNews.vue
created() {
    const newsData = this.$route.params.newsData;
}
```


**TODO**:搜索的按下空格触发不能正常运行

## 前后端对接

后端给出:
- 筛选条件:前端可以实现包括多选框,下拉选择,输入框,标签,时间选择等.即在前端选择好条件后后端可以返回符合条件的项目
- 数据属性:文本,数字,时间,图片,标签等,将标题,作者,标签作为一个list返回,方便作为搜索的提示
- 数据量大则搜索向后端发送信息,后端返回符合条件的数据,数据量小则前端获取所有数据,在前端进行搜索

**关键字搜索**:如果数据量小则在前端完成(check),此时自动补全也是可用的,否则向后端发送关键字,后端返回符合条件的数据


## 部署
