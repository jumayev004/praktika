import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;

public class NameCollectionApp {

    private static final String DB_URL = "jdbc:postgresql://localhost:5432/your_database"; // Замените на ваш URL
    private static final String USER = "your_username"; // Замените на ваше имя пользователя
    private static final String PASSWORD = "your_password"; // Замените на ваш пароль

    public static void main(String[] args) {
        List<String> collection1 = new ArrayList<>();
        List<String> collection2 = new ArrayList<>();

        // Заполнение коллекций
        collection1.add("Alice");
        collection1.add("Bob");
        collection2.add("Charlie");
        collection2.add("Diana");

        // Сохранение в базу данных
        saveNamesToDatabase(collection1);
        saveNamesToDatabase(collection2);

        // Вывод имен на консоль
        System.out.println("Collection 1:");
        collection1.forEach(System.out::println);
        System.out.println("Collection 2:");
        collection2.forEach(System.out::println);
    }

    private static void saveNamesToDatabase(List<String> names) {
        String insertSQL = "INSERT INTO names (name) VALUES (?)";

        try (Connection connection = DriverManager.getConnection(DB_URL, USER, PASSWORD);
             PreparedStatement preparedStatement = connection.prepareStatement(insertSQL)) {

            for (String name : names) {
                preparedStatement.setString(1, name);
                preparedStatement.executeUpdate();
            }

        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}


CREATE TABLE names (

    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL
);
