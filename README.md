import java.io.FileOutputStream;  
import java.io.IOException;  
import org.apache.poi.*;  
public class Jala {
	public static void main(String[] args) throws IOException {
		
		XSSFWorkbook workbook = new XSSFWorkbook();
        XSSFSheet sheet = workbook.createSheet("Details");
         
        Object[][] details = {
                {"Sai", 19},
                {"Yeshwanth", 18},
                {"John", 22},
        };
 
        int rowCount = 0;
         
        for (Object[] name : details) {
            Row row = sheet.createRow(++rowCount);
             
            int columnCount = 0;
             
            for (Object field : name) {
                Cell cell = row.createCell(++columnCount);
                if (field instanceof String) {
                    cell.setCellValue((String) field);
                } else if (field instanceof Integer) {
                    cell.setCellValue((Integer) field);
                }
            }
             
        }
         
         
        try (FileOutputStream outputStream = new FileOutputStream("Details.xlsx")) {
            workbook.write(outputStream);
        }
		
	}
}
