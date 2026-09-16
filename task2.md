1. **Interface Segregation Principle**: A class should not be forced to depend on methods it does not use.
    - `LoanPayment` is forced to inherit `initiatePayments()` even though it doesn't support the operation
    - `BankPayment` is forced to inherit `initiateLoanSettlement()` and `initiateRePayment()` even though it doesn't support either operation
    - To solve this, the method `initiatePayments()` should only exist inside the `BankPayment` interface, and the `initiateLoanSettlement()` and `initiateRePayment()` methods should only exist inside the `LoanPayment` interface.
2. **Liskov Substitution Principle**: Objects of a subtype should be usable wherever objects of the parent type are expected without breaking the program's expected behavior.
    - `initiatePayments()` should be callable by any instance of `Payment`, according to the interface. However, if a `BankPayment` tries to call it, it breaks the program.
    - `initiatePayments()` should not even be callable by `BankPayment`. See the solution in `1.` to solve this.
3. **Single Responsibility Prinicple**: A class or interface should have one reason to change.
    - `Payment` represents bank payments, loan settlements, loan repayments, and potentially additional repayment options. So to change one category of payment could force changes to the common `Payment` interface and potentially all of its implementation.
    - Since this is a consequence of the ISP violation, the solution to `1.` also solves this.