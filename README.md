This program simulates a water tank management system using JOptionPane for input and output. The user can choose between two types of tanks:

HomeTank → a small tank (up to 200 liters).

BuildingTank → a large tank (up to 1000 liters).

The program allows the user to:

Fill the tank with a chosen amount of water.

Use water from the tank.

Check the tank’s status → showing if it is Full, Empty, or In Use (partially filled).

The status updates after each action, helping the user monitor the current water level.

Abstract Methods:
<img width="1027" height="403" alt="image" src="https://github.com/user-attachments/assets/3565b666-9667-48ec-af3e-ee4ada38703e" />

Subclasses: HomeTank and BuildingTank are the two subclasses of class water. Both subclasses implement the capacity (200 liters for HomeTank and 1000 liters for BuildingTank) and override the abstract methods to manage water levels.






import javax.swing.JOptionPane;


public class water {
    int capacity;
    int currentLevel;

    public water(int capacity) {
        this.capacity = capacity;
        this.currentLevel = 0;
    }

    // Adds water to the tank
    public void fillTank(int liters) {
        currentLevel += liters;
        if (currentLevel > capacity) currentLevel = capacity;
        JOptionPane.showMessageDialog(null, "Level: " + currentLevel + "/" + capacity);
    }

    // Uses water from the tank
    public void useWater(int liters) {
        currentLevel -= liters;
        if (currentLevel < 0) currentLevel = 0;
        JOptionPane.showMessageDialog(null, "Level: " + currentLevel + "/" + capacity);
    }

    // Checks the tank status
    public void checkStatus() {
        if (currentLevel == 0) JOptionPane.showMessageDialog(null, "Empty");
        else if (currentLevel == capacity) JOptionPane.showMessageDialog(null, "Full");
        else JOptionPane.showMessageDialog(null, "In Use");
    }

    // Main program
    public static void main(String[] args) {
        String choice = JOptionPane.showInputDialog("1. HomeTank (200)\n2. BuildingTank (1000)");
        int cap = choice.equals("1") ? 200 : 1000;

        water tank = new water(cap);

        while (true) {
            String action = JOptionPane.showInputDialog("1. Fill\n2. Use\n3. Status\n4. Exit");

            if (action.equals("1")) {
                int liters = Integer.parseInt(JOptionPane.showInputDialog("Liters to fill:"));
                tank.fillTank(liters);
            } else if (action.equals("2")) {
                int liters = Integer.parseInt(JOptionPane.showInputDialog("Liters to use:"));
                tank.useWater(liters);
            } else if (action.equals("3")) {
                tank.checkStatus();
            } else if (action.equals("4")) {
                JOptionPane.showMessageDialog(null, "Program Ended.");
                break;
            }

            // If tank is full or empty, show status and end program
            if (tank.currentLevel == 0 || tank.currentLevel == tank.capacity) {
                tank.checkStatus();
                JOptionPane.showMessageDialog(null, "Program Ended.");
                break;
            }
        }
    }
}



<img width="1020" height="546" alt="image" src="https://github.com/user-attachments/assets/937d7c4c-286e-4004-85b2-04e1c4bbe506" />
<img width="1024" height="523" alt="image" src="https://github.com/user-attachments/assets/6decff24-5eb8-487a-b5f1-9b36e56a0fe2" />
<img width="1041" height="573" alt="image" src="https://github.com/user-attachments/assets/55ed8d73-d806-4902-94bf-f4c2f58d57cd" />
<img width="1053" height="550" alt="image" src="https://github.com/user-attachments/assets/3bf01c6a-9388-42a3-9ff4-01b2dbfdd217" />
<img width="1009" height="538" alt="image" src="https://github.com/user-attachments/assets/1d8343d5-edf5-4131-87b6-985a3ebc683b" />







