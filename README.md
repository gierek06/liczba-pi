# liczba-pi2


import java.math.BigDecimal;
import java.math.MathContext;
import java.math.BigInteger;

import static java.lang.Math.pow;

public class liczbapi2 {
    static BigDecimal countPi(int n) {
        BigDecimal pi = BigDecimal.valueOf(0);
        for (int i = 0; i < n; i++) {
            BigDecimal a = BigDecimal.valueOf(4).divide(BigDecimal.valueOf((8 * i + 1)), MathContext.DECIMAL128);
            BigDecimal b = BigDecimal.valueOf(2).divide(BigDecimal.valueOf(8 * i + 4), MathContext.DECIMAL128);
            BigDecimal c = BigDecimal.valueOf(1).divide(BigDecimal.valueOf(8 * i + 5), MathContext.DECIMAL128);
            BigDecimal d = BigDecimal.valueOf(1).divide(BigDecimal.valueOf(8 * i + 6), MathContext.DECIMAL128);
            BigDecimal sub = a.subtract(b).subtract(c).subtract(d);
            BigDecimal mul = BigDecimal.valueOf(pow(16, i)).multiply(sub);
            BigDecimal res = BigDecimal.valueOf(1).divide(mul, MathContext.DECIMAL128);
            pi = pi.add(res);
        }
        return pi;
    }

    public static void main(String[] args) {

        System.out.println(countPi(10).toString());
    }

}
