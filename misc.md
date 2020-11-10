# EAN-13条码/条形码校验码生成【Java】
```Java
  private static long genCheckDigit(long n) {
        String in = String.valueOf(n);
        int evens = 0; 
        int odds = 0; 
        int checkSum; 
  
        for (int i = 0; i < in.length(); i++) {
            int digit = Integer.parseInt(String.valueOf(in.charAt(i)));
            if(0==(i % 2)) {//相当于i从1开始的奇数位置
                odds+=digit;   
            }else {
                evens+=digit;
            }
        }

        checkSum=(evens*3+odds) % 10;
        if(0!=checkSum) {
            checkSum=10-checkSum; 
        }
        return checkSum;
    }
```
根据[此规则](https://www.open.edu/openlearn/science-maths-technology/exploring-communications-technology/content-section-2.1)编写的代码。
代码的输出利用以下两个在线工具核对过：

* http://www.free-barcode.com/EanCheckCode/index.htm
* http://www.axicon.com/checkdigitcalculator.html
