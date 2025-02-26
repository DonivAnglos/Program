import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

import java.time.Duration;

public class Flum {

	public static void main(String[] args) {
		WebDriver driver = new ChromeDriver();
		driver.get("https://pp-web.flurn.in/login");
		WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(10));
		WebElement phoneField = wait.until(ExpectedConditions.presenceOfElementLocated(By.name("phone")));
		phoneField.sendKeys("9663824637");
		WebElement getOtpButton = driver.findElement(By.xpath("//button[text()='Get OTP']"));
		getOtpButton.click();
		WebElement otpField = wait.until(ExpectedConditions.presenceOfElementLocated(By.name("otp")));
		otpField.sendKeys("565656"); 
		WebElement loginButton = driver.findElement(By.xpath("//button[contains(text(), 'Login')]"));
		loginButton.click();
		wait.until(ExpectedConditions.urlContains("dashboard"));
		System.out.println("Login successful!");
		driver.quit();
	}
}
