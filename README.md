# **Tweet App Ruby on Rails**

> Halo! ini adalah project Tweet App menggunakan Ruby on Rails. Yuk kita mulai aja dengan langkah-langkah dibawah ini!

## **A. Setup Rails Apps**

### 1. Install Ruby on Rails

```console
rails new tweet-app
```
### 2. Run tweet-app

```console
rails s
```
## **B. Setup Controller Home**

### 1. Membuat Controller Home

```console
rails g controller home top
```

```ruby
class HomeController < ApplicationController
  def top
  end
end
```

> artinya: membuat controller `home` yang di dalamnya ada `action` (method) `top`

### 2. Setting Routes

Tambahkan action `top`, jadi ketika mengakses url `home/top` maka akan di panggil controller `home` dengan action (method) `top`

```ruby
Rails.application.routes.draw do
  get '/top' => 'home#top'
end
```

### 3. Tambahkan Content Top

Tambahkan kode HTML ini di dalam file `views/home/top.html.erb`
```HTML
<header>
  <div class="header-logo">
    <a href="/">TweetApp</a>
  </div>
  <ul class="header-menus">
    <li><a href="/about">About</a></li>
  </ul>
</header>
<div class="main top-main">
  <div class="top-message">
    <h2>Tweet to the world.<br>Connect to the world.</h2>
    <p>Share your favorite moments!</p>
  </div>
</div>
```

### 4. Tambahkan Method About

Tambahkan action (method) `about` di controllers `home_controller.rb`
```ruby
class HomeController < ApplicationController
  def top
  end

  def about
  end
end
```

### 5. Tambahkan Content About

Tambahkan HTML pada `views/home/about.html.erb`
```HTML
<header>
  <div class="header-logo">
    <a href="/">TweetApp</a>
  </div>
  <ul class="header-menus">
    <li><a href="/about">About</a></li>
  </ul>
</header>
<div class="about-main">
  <h2>About TweetApp</h2>
  <p>
    TweetApp is a social networking service.
    Users can post and interact with short messages called "tweets".
  </p>
</div>
```

### 6. Tambahkan Routes About

Tambahkan `get` `/about` yang mengakses controller `home` dengan action `about`
```ruby
Rails.application.routes.draw do
  get '/top' => 'home#top'
  get '/about' => 'home#about'
end
```

## **C. Styling I**

### 1. Tambahkan Code CSS

Tambahkan `code` css ini di `home.scss`
```scss
* {
    box-sizing: border-box;
  }
  
  html {
    font: 100%/1.5 'Avenir Next', 'Hiragino Sans', sans-serif;
    line-height: 1.7;
    letter-spacing: 1px;
  }
  
  ul, li {
    list-style-type: none;
    padding: 0;
    margin: 0;
  }
  
  a {
    text-decoration: none;
    color: #2d3133;
    font-size: 14px;
  }
  
  h1, h2, h3, h4, h5, h6, p {
    margin: 0;
  }
  
  input {
    background-color: transparent;
    outline-width: 0;
  }
  
  form input[type="submit"] {
    border: none;
    cursor: pointer;
  }
  
  /* Common Layout ================================ */
  body {
    color: #2d3133;
    background-color: #3ecdc6;
    margin: 0;
    min-height: 1vh;
  }
  
  .main {
    position: absolute;
    top: 64px;
    width: 100%;
    height: auto;
    min-height: 100%;
    background-color: #f5f8fa;
  }
  
  .container {
    max-width: 600px;
    margin: 60px auto;
    padding-left: 15px;
    padding-right: 15px;
    clear: both;
  }
  
  /* Header ================================ */
  header {
    height: 64px;
    position: absolute;
    z-index: 1;
    width: 100%;
  }
  
  .header-logo {
    float: left;
    padding-left: 20px;
    color: white;
    font-size: 22px;
    line-height: 64px;
  }
  
  .header-logo a{
    color: white;
    font-size: 22px;
  }
  
  .header-menus {
    float: right;
    padding-right: 20px;
  }
  
  .header-menus li {
    float: left;
    line-height: 64px;
    font-size: 13px;
    color: white;
    padding-left: 15px;
  }
  
  .header-menus a {
    float: left;
    font-size: 13px;
    color: white;
  }
  
  .header-menus .fa {
    padding-right: 5px;
  }
  
  .header-menus input[type="submit"] {
    padding: 0 20px;
    float: left;
    line-height: 64px;
    color: white;
    margin: 0;
    font-size: 13px;
  }
  
  /* Top ================================ */
  .top-main {
    padding: 200px 0 100px;
    text-align: center;
    position: absolute;
    top: 0;
    width: 100%;
    height: auto;
    min-height: 100%;
    color: white;
    background-color: #3ecdc6;
    background-repeat: no-repeat;
    background-position: center 50%;
    background-size: cover;
    background-image: url("/top.jpeg");
  }
  
  .top-message {
    position: relative;
  }
  
  .top-main h2 {
    font-size: 70px;
    font-weight: 500;
    line-height: 1.3;
    -webkit-font-smoothing: antialiased;
    margin-bottom: 20px;
  }
  
  .top-main p {
    font-size: 24px;
  }
  
  /* About ================================ */
  .about-main {
    padding: 180px 8% 0;
    color: white;
  }
  
  .about-main h2 {
    font-size: 64px;
    font-weight: 500;
    line-height: 1.4;
  }
  
  .about-main p {
    font-weight: 200;
    font-size: 20px;
  }
  
  .about-img {
    width: 84%;
  }
  
  /* Form ================================ */
  .form {
    max-width: 600px;
    margin: 0 auto;
    background-color: white;
    box-shadow: 0 2px 6px #c1ced7;
  }
  
  .form-heading {
    font-weight: 300;
    margin: 60px 0 20px;
    font-size: 48px;
    color: #bcc8d4;
  }
  
  .form-body {
    padding: 30px;
  }
  
  .form-error {
    color: #ff4d75;
  }
  
  .form input {
    width: 100%;
    border: 1px solid #d8dadf;
    padding: 10px;
    color: #57575f;
    font-size: 16px;
    letter-spacing: 2px;
    border-radius: 2px;
  }
  
  .form textarea {
    width: 100%;
    min-height: 110px;
    font-size: 16px;
    letter-spacing: 2px;
  }
  
  .form input[type="submit"] {
    background-color: #3ecdc6;
    color: white;
    cursor: pointer;
    font-weight: 300;
    width: 120px;
    border-radius: 2px;
    margin-top: 8px;
    margin-bottom: 0;
    float: right;
  }
  
  .form-body:after {
    content: '';
    display: table;
    clear: both;
  }
  
  /* Flash ================================ */
  .flash {
    padding: 10px 0;
    color: white;
    background: rgb(251, 170, 88);
    text-align: center;
    position: absolute;
    top: 64px;
    z-index: 10;
    width: 100%;
    border-radius: 0 0 2px 2px;
    font-size: 14px;
  }
```

Tambahkan `top.jpeg` background di top-main `home.scss`

```scss
  /* top main */
  background-image: url("/top.jpeg");
```

### 2. Tambahkan Gambar Tweets

Tambahkan `tweets.png` di content `about.html.erb`.
```HTML
<header>
  <div class="header-logo">
    <a href="/">TweetApp</a>
  </div>
  <ul class="header-menus">
    <li><a href="/about">About</a></li>
  </ul>
</header>
<div class="about-main">
  <h2>About TweetApp</h2>
  <p>
    TweetApp is a social networking service.
    Users can post and interact with short messages called "tweets".
  </p>
  <img class="about-img" src="/tweets.png">
</div>
```

## **D. Displaying Posts**

### 1. Buat Controller Post

Tambahkan controller `Post` dengan action `index`

```console
rails g controller Post index
```

```ruby
class PostController < ApplicationController
  def index
  end
end
```

### 2. Tambahkan di Routes

Tambahkan `get` di routes untuk `post/index`

```ruby
Rails.application.routes.draw do
  get '/top' => 'home#top'
  get '/about' => 'home#about'
  get '/post/index' => 'post#index'
end
```

### 3. Tambahkan Post di Header

Tambahkan `Posts` di setiap `header`
```HTML
<header>
  <div class="header-logo">
    <a href="/">TweetApp</a>
  </div>
  <ul class="header-menus">
    <li><a href="/about">About</a></li>
    <li><a href="/post/index">Posts</a></li>
  </ul>
</header>
```

### 4. Tambahkan Content Post

Tambahkan `HTML` ini di `views/post/index.html.erb`

```HTML
<header>
  <div class="header-logo">
    <a href="/">TweetApp</a>
  </div>
  <ul class="header-menus">
    <li>
      <a href="/about">About</a>
    </li>
    <li>
      <a href="/post/index">Posts</a>
    </li>
  </ul>
</header>

<div class="main posts-index">
  <div class="container">
    <div class="posts-index-item">
      Learning Rails with Progate!
    </div>
    <div class="posts-index-item">
      Trying to display the posts!
    </div>
  </div>
</div>
```

### 5. Tambahkan Code CSS

Tambahkan code `css` ini di `post.scss`
```scss
.posts-index-item {
    padding: 20px 30px;
    background-color: white;
    overflow: hidden;
    box-shadow: 0 2px 6px #c1ced7;
  }
  
  .post-left img {
    width: 50px;
    height: 50px;
    border-radius: 40%;
    box-shadow: 0 2px 6px #c1ced7;
    object-fit: cover;
  }
  
  .post-user-name a {
    font-weight: 600;
  }
  
  .post-user-name a:hover {
    color: #3ecdc6;
  }
  
  .post-left {
    float: left;
    width: 10%;
  }
  
  .post-right {
    float: left;
    width: 90%;
    padding-left: 25px;
    text-align: left;
  }
  
  /* posts/show ================================ */
  .posts-show form {
    display: inline;
  }
  
  .posts-show-item {
    padding: 30px;
    background-color: white;
    box-shadow: 0 2px 6px #c1ced7;
    overflow: hidden;
  }
  
  .posts-show-item img {
    width: 60px;
    height: 60px;
    border-radius: 40%;
    box-shadow: 0 2px 6px #c1ced7;
    vertical-align: middle;
    object-fit: cover;
  }
  
  .posts-show-item .post-user-name a {
    vertical-align: middle;
    font-size: 24px;
    margin-left: 15px;
  }
  
  .posts-show-item p {
    font-size: 24px;
    margin: 20px 0;
  }
  
  .post-time {
    color: #8899a6;
    margin-bottom: 10px;
  }
  
  .post-menus {
    float: right;
  }
  
  .post-menus a, .post-menus input {
    color: #8899a6;
    text-decoration: underline;
    font-size: 14px;
  }
  
  /* posts/new ================================ */
  .posts-new textarea {
    font-size: 20px;
    padding: 10px;
    min-height: 140px;
    border: 1px solid rgb(216, 218, 223);
    resize: none;
  }
  
  .posts-new textarea::-webkit-input-placeholder {
    font-size: 24px;
    opacity: 0.5;
  }
```

### 6. Tambahkan Variables di Views

Tambahkan `post1` dan `post2` di `index.html.erb`

```HTML
<header>
  <div class="header-logo">
    <a href="/">TweetApp</a>
  </div>
  <ul class="header-menus">
    <li>
      <a href="/about">About</a>
    </li>
    <li>
      <a href="/post/index">Posts</a>
    </li>
  </ul>
</header>

<% post1 = "Learning Rails with Progate!" %>
<% post2 = "Trying to display the posts!" %>

<div class="main posts-index">
  <div class="container">
    <div class="posts-index-item">
      <%= post1 %>
    </div>
    <div class="posts-index-item">
      <%= post2 %>
    </div>
  </div>
</div>
```

### 7. Menggunakan `each` Method di Views

```HTML
<!-- Header -->
<% posts = [
      "Learning Rails with Progate!",
      "Trying to display the posts!"
    ]
%>

<div class="main posts-index">
  <div class="container">
    <% posts.each do |post| %>
    <div class="posts-index-item">
      <%= post %>
    </div>
    <% end %>
  </div>
</div>
```

### 8. Defining Variables in Actions

Memindahkan menjadi ke action `index` di controller Post
```ruby
class PostController < ApplicationController
  def index
    @posts = [
        "Learning Rails with Progate!",
        "Trying to display the posts!"
    ]
  end
end
```

```HTML
<!-- Header -->
<div class="main posts-index">
  <div class="container">
    <% @posts.each do |post| %>
    <div class="posts-index-item">
      <%= post %>
    </div>
    <% end %>
  </div>
</div>
```

## **E. Menggunakan Database**

### 1. Membuat Migration file

```console
rails g model Post content:text
```

```ruby
class Post < ApplicationRecord
end
```

> `Post`: mesti singular, `content`: adalah nama column, `text`: data type

### 2. Membuat Table

Dengan cara menggunakan `rails db:migrate`

```console
rails db:migrate
```

### 3. Rails console

```console
rails console
Loading development environment (Rails 5.0.3)
[1] pry(main)> 1 + 1
=> 2
[2] pry(main)>
```

### 4. Tambahkan Data ke Table

```console
rails console
.
.
> post1 = Post.new(content: "Learning Rails with Progate!")
> post1.save
```

### 5. Mendapatkan Data dari Table

```console
rails console
.
.
> post = Post.first
> post.content
=> "Learning Rails..."
```

### 6. Mendapatkan Data All dari Table

```console
rails console
.
.
> post = Post.all
# maka isinya akan array
```

```console
rails console
.
.
> post = Post.all[0].content
=> "Learning Rails..."
```

### 7. Menampilkan Posts

```ruby
class PostController < ApplicationController
  def index
    @posts = Post.all
  end
end
```

```HTML
<!-- Header -->
<div class="main posts-index">
  <div class="container">
    <% @posts.each do |post| %>
    <div class="posts-index-item">
      <%= post.content %>
    </div>
    <% end %>
  </div>
</div>
```

## **F. Refactoring Layout**

### 1. Memindahkan `header` ke `application.html.erb`

Hapus semua header di `views` kemudian, buat hanya satu di `applications.html.erb`

```HTML
<header>
  <div class="header-logo">
    <a href="/">TweetApp</a>
  </div>
  <ul class="header-menus">
    <li>
      <a href="/about">About</a>
    </li>
    <li>
      <a href="/post/index">Posts</a>
    </li>
  </ul>
</header>
```

### 2. Ganti anchor link
```HTML
<header>
  <div class="header-logo">
    <%= link_to("TweetApp","/") %>
  </div>
  <ul class="header-menus">
    <li>
    <%= link_to("About","/about") %>
    </li>
    <li>
    <%= link_to("Posts","/post/index") %>
    </li>
  </ul>
</header>
```