package Assignment;

import java.util.concurrent.TimeUnit;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import io.github.bonigarcia.wdm.WebDriverManager;

public class WebTable {
    static WebDriver driver = null;

    public static void main(String[] args) {
        // Setup WebDriverManager for ChromeDriver
       
        try {
            driver = new ChromeDriver();
            driver.get("https://www.w3schools.com/html/html_tables.asp");
            driver.manage().window().maximize();
            driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
            driver.manage().timeouts().pageLoadTimeout(10, TimeUnit.SECONDS);
            String value = "Mexico";

            boolean val = checkWhetherValueIsPresentInWebTable(value);
            System.out.println("Value found: " + val);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            if (driver != null) {
                driver.quit(); // Ensure the driver quits even if an exception occurs
            }
        }
    }

    public static boolean checkWhetherValueIsPresentInWebTable(String value) {
        int rowCount = driver.findElements(By.xpath("//table[@id='customers']//tr")).size();
        int colCount = driver.findElements(By.xpath("//table[@id='customers']//th")).size();
        boolean checkPoint = false;

        // Loop through each row
        for (int i = 1; i < rowCount; i++) { // Start from 1 to skip the header row
            // Loop through each column
            for (int j = 1; j <= colCount; j++) { // Use <= to include the last column
                // Get the cell value
                String Val = driver.findElement(By.xpath("//table[@id='customers']//tr[" + (i + 1) + "]//td[" + j + "]")).getText();
                // Check if the cell value matches the desired value
                if (Val.equalsIgnoreCase(value)) {
                    checkPoint = true;
                    break; // Break out of the inner loop if the value is found
                }
            }
        }
		return checkPoint;
    }
