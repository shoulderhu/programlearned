<a id="top"></a>

### java Web 學習紀錄

#### <a href="#s1">servlet 常用功能</a>
#### <a href="#s2">jsp 常用功能</a>

#### <a id="s1" href="#top">servlet 常用功能(需在 doget or dopost 裡面)</a>
- PrintWriter(輸出至網頁)
    ```java
        response.setContentType("text/html;charset=UTF-8");
        PrintWriter out = response.getWriter();
        out.println("<script type=\"text/javascript\">");
        out.println("alert('帳號或密碼輸入錯誤,請重新輸入');");
        out.println("location='login.jsp';");
        out.println("</script>");
    ```
- 各個所限範圍
    - request :     HTTP請求開始到結束這段時間
    - session :     HTTP會話開始到結束這段時間
    - application : 伺服器啟動到停止這段時間

- request
    - 取得傳遞參數:String passwd = request.getParameter("passwd");
    - 導引至某網頁:request.getRequestDispatcher("login.jsp").forward(request, response);

- cookie
    - 接收cookie
        ```java
            Cookie[] cookies = request.getCookies();
            if(cookies!=null) {			
                for(Cookie c:cookies ) {
                    String name = c.getName();
                    String value = c.getValue();
                    //把cookie存入
                    map.put(name, value);				
                }
            }
        ```
    - 設定cookie
        ```java
            //設一個cookie:name:ming
            Cookie cookieAccount = new Cookie("account","ming");
            //設定cookie生命存放時間(秒)
            cookieAccount.setMaxAge(1*60);
            response.addCookie(cookieAccount);
        ```

- session
    - 取得session : HttpSession session = request.getSession(); 
    - 取得session裡的傳遞參數 : String user=(String)session.getAttribute("user");
    - 設定session參數 : session.setAttribute("user", user);
    - 刪除session參數 : session.removeAttribute("user");

- application
    - 取得參數 : application.getAttribute("x");
    - 設定參數 : application.setAttribute("x", x);

- jdbc
    - 1.註冊jdbc : Class.forName("com.mysql.jdbc.Driver");
    - 2.新增連線參數 Properties 
        ```java
            Properties prop = new Properties();
            prop.setProperty("user", "root");
            prop.setProperty("password", "root");
        ```
    - 3.新增連線 : Connection conn = DriverManager.getConnection("jdbc:mysql://localhost(ip):3306(port)/attractions(資料庫名稱)",prop(屬性));
    - 4.新增sql子句參數 : 
        - 1.update
            ```java
                String sql = "UPDATE manager SET passwd=? WHERE user=?";
                PreparedStatement pstmt=conn.prepareStatement(sql);
                pstmt.setString(1, passwd);
                pstmt.setString(2, user);
                pstmt.executeUpdate();
            ```
        - 2.delete
            ```java
                String sql = "DELETE FROM member WHERE user=?";
                PreparedStatement pstmt=conn.prepareStatement(sql);
                pstmt.setString(1,user);
			    pstmt.execute();
            ```
        - 3.query
            ```java
                String sql = "SELECT * FROM manager where user=? and passwd=?";
                PreparedStatement pstmt=conn.prepareStatement(sql);	
                pstmt.setString(1, user);
				pstmt.setString(2, passwd);
				ResultSet rs = pstmt.executeQuery();
                while(rs.next()){
                    rs.getString("資料欄位名稱")
                }
            ```
        - 4.insert
            ```java
                String insql = "INSERT INTO member(user,passwd,authority,email) values(?,?,?,?)";
                PreparedStatement pstmt=conn.prepareStatement(insql);
                pstmt.setString(1, user);
                pstmt.setString(2, passwd);
                pstmt.setString(3,"0");
                pstmt.setString(4,email);
                pstmt.execute();
            ```

#### <a id="s2" href="#top">jsp 常用功能</a>
- import java包 : <%@page import="java.util.*" %>

- form表單
    - action : 導引至該名稱的java程式檔
    - method : 使用甚麼方式傳遞
    - input  : 利用name來傳遞給java(servlet)參數，最後進行submit
    ```html
        <form  action="loginMember"  method='post'>
            <input type="text"  name="user" class="form-control"  placeholder="請輸入帳號">
            <input type="password" name="passwd"  class="form-control" placeholder="請輸入密碼" >
            <input type="submit" class="btn btn-default" style="color:black;font-weight: 900;" value="登入"/>
        </form>
    ```

- 註冊為errorPage
    ```jsp
        <%@page isErrorPage="true" %>
        <body><%out.print(exception);%></body>
    ```

- include jsp
    ```jsp
    <body>
        <!-- 需注意文件結構,不一定要用jsp也可以用html -->>
        <%@include file="Jsp09header.html" %>
        Main Page
        <hr/>
        <%@include file="Jsp09footer.jsp" %>
    </body>
    ```

<a href="#top">回 Top</a>
