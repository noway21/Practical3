# #include <stdio.h>

long long countNumbers(int r) {
    long long dp[2][2]; 
    dp[0][0] = 1; 
    dp[0][1] = 1; 
    
    for (int i = 1; i < r; i++) {
        dp[i % 2][0] = dp[(i - 1) % 2][1]; 
        dp[i % 2][1] = dp[(i - 1) % 2][0] + dp[(i - 1) % 2][1]; 
    }
    
    return dp[(r - 1) % 2][0] + dp[(r - 1) % 2][1]; 
}

int main() {
    int r;
    printf("Введіть кількість розрядів (р ≤ 30): ");
    scanf("%d", &r);
    
    if (r <= 0 || r > 30) {
        printf("Некоректне вхідне значення!\n");
        return 1;
    }
    
    long long result = countNumbers(r);
    printf("Кількість чисел із %d розрядами, де 5 та 9 не стоять поруч: %lld\n", r, result);
    
    return 0;
}
