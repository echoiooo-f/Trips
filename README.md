# 寒假回国路线簿（独立版）

不用登录，打开网址就能看、能改，两个人的改动实时同步。

- 网页放在 GitHub Pages 上
- 数据存在 Supabase（免费的在线数据库）里

整个设置大约 20–30 分钟，只需要做一次。

---

## 第 1 步：建数据库（Supabase）

1. 打开 https://supabase.com ，点 **Start your project**，选 **Continue with GitHub** 登录。
2. 点 **New project**：
   - Name 随便填，比如 `winter-trip`
   - Database Password 点 Generate 自动生成就行（这个页面用不到它）
   - Region 选离你们近的，比如 `East US` 或 `Singapore`
   - 点 **Create new project**，等一两分钟。
3. 左边栏点 **SQL Editor**，把 `setup.sql` 的全部内容粘贴进去，点右下角 **Run**。
   看到 `Success` 就好了。这一步会建好表，并把现在的行程、待办和攻略都导进去。
4. 左边栏点 **Project Settings**（齿轮）→ **API Keys** / **Data API**，记下两样东西：
   - **Project URL**：形如 `https://xxxx.supabase.co`
   - **anon / publishable key**：可以公开的那个
   - ⚠️ 不要用 `service_role` 或 `secret` key。

## 第 2 步：填配置

打开 `config.js`，把两项填进去：

```js
window.TRIP_CONFIG = {
  url: 'https://xxxx.supabase.co',
  key: '你的 anon / publishable key'
};
```

## 第 3 步：放到 GitHub Pages

1. 在 GitHub 新建一个仓库，比如 `winter-trip`。
2. 把 `index.html`、`config.js`、`README.md` 三个文件传上去：
   仓库页面 **Add file → Upload files**，拖进去，点 **Commit changes**。
   （`setup.sql` 不用传，它只在第 1 步用一次。）
3. 仓库 **Settings → Pages**：
   - Source 选 **Deploy from a branch**
   - Branch 选 `main`，文件夹选 `/ (root)`，点 **Save**
4. 等一两分钟，页面顶部会出现网址，形如
   `https://你的用户名.github.io/winter-trip/`
   把这个网址发给他就行。

---

## 需要知道的

- **谁拿到网址谁就能改**：不要转发到群里或公开的地方。
- **仓库是公开的**：免费账号的 GitHub Pages 需要公开仓库，别人能看到 `config.js` 里的地址和密钥。
  行程内容本身不在仓库里，而是存在 Supabase。想把仓库设成私有，可以用 GitHub 学生包里免费的 GitHub Pro。
- **Supabase 免费项目一周没人访问会自动暂停**：到 Supabase 后台点 **Restore** 就能恢复，数据还在。
  出发前和旅行中你们会经常打开，一般不会遇到。
- **以后要改页面功能**：把新的 `index.html` 重新上传覆盖就行，数据不受影响。
