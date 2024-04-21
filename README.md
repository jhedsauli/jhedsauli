package loanmanagement;
import javax.swing.*;
import java.util.ArrayList;
import java.util.List;

public class LoanManagementSystem {
	public static void main(String[] args) {
        LoanManagementSystem system = new LoanManagementSystem();
        Borrower borrower = new Borrower("John", 20000);
        Loan loan = system.applyForLoan(borrower, 50000);
        if (loan != null) {
            JOptionPane.showMessageDialog(null, "Loan approved for " + borrower.getName() + " with amount " + loan.getAmount());
        } else {
            JOptionPane.showMessageDialog(null, "Loan application rejected for " + borrower.getName());
        }
    }

    private Loan applyForLoan(Borrower borrower, int amount) {
        PreAssessment preAssessment = new PreAssessment();
        if (preAssessment.isEligible(borrower, amount)) {
            return new Loan(borrower, amount);
        }
        return null;
    }
}
