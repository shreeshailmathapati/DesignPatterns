# DesignPatterns

#   C#:  18th -Jul -2022

// Sample code and identify problems w.r.t. patterns

class Checker 
{
    static bool batteryIsOk(float temperature, float soc, float chargeRate) {
        if(temperature < 0 || temperature > 45) {
            Console.WriteLine("Temperature is out of range!");
            return false;
        } else if(soc < 20 || soc > 80) {
            Console.WriteLine("State of Charge is out of range!");
            return false;
        } else if(chargeRate > 0.8) {
            Console.WriteLine("Charge Rate is out of range!");
            return false;
        }
        return true;
    }

Problem:  Method batteryIsOk is handling 3 different types of scenarios or responsibilities temperature range, soc and chargeRate and voilating single responsibility pattern

#############################################################################################
Refactored Code:

class Checker
{
    //delegate
    bool batteryIsOk(float temperature, float soc, float chargeRate) {
    bool isTemperatureValid = new isTemperatureOk(temperature);
    bool isSocValid         = new isSocOk(soc);
    bool ischargeRateValid  = new ischargeRateOk(chargeRate);   
    }
     
    // Method to check temperature range
    bool isTemperatureOk(float temperature)
    {
        if(temperature < 0 || temperature > 45) {
            printMessage("Temperature is out of range!");
            return false;
        }
        return true;
    }
    
    // Method to check State of Charge
    bool isSocOk(float soc)
    {
        if(soc < 20 || soc > 80) {
           printMessage("State of Charge is out of range!");
           return false;
        }
        return true;
    }
    
    // Method to check Charge Rate
    bool ischargeRateOk(float chargeRate)
    {
        if(soc < 20 || soc > 80) {
           printMessage("State of Charge is out of range!");
           return false;
        }
        return true;
    }
    
    // Method to print message of each battery status
    void printMessage(string message)
    {
        Console.WriteLine(message);
    }
}

# C#:  18th -Jul -2022
#############################################################################################
