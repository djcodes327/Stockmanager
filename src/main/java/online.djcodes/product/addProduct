package online.djcodes.product;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;
import java.sql.*;

@WebServlet(name = "addProduct")
public class addProduct extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            PrintWriter out = response.getWriter();
            Connection connection;
            Class.forName("com.mysql.jdbc.Driver");
            connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/stockmanager","root","");
            //Parameters
            String productName = request.getParameter("pname");
            String productPrice = request.getParameter("pprice");
            String productQuantity = request.getParameter("pquantity");
            String productDescription = request.getParameter("pdescription");
            String sid = (String) request.getParameter("storeid");



            PreparedStatement ps = connection.prepareStatement("insert into sm_products(pname,pprice,pquantity,pdescription,storeid)values(?,?,?,?,?)");
            ps.setString(1,productName);
            ps.setString(2,productPrice);
            ps.setString(3,productQuantity);
            ps.setString(4, productDescription );
            ps.setString(5,sid);

            ps.executeUpdate();


            out.print("<script> alert(\"Product Added Successfully\"); </script>");

            RequestDispatcher rd = request.getRequestDispatcher("products.jsp");
            rd.include(request, response);




        }
        catch(Exception e) {
            PrintWriter out = response.getWriter();
            out.print("Exception"+e);
        }

    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {

    }
}
