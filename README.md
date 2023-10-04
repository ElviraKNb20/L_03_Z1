# L_03_Z1
import java.util.ArrayList;

class Airline {
    private String destination;
    private int flightNumber;
    private String aircraftType;
    private String departureTime;
    private String dayOfWeek;

    public Airline(String destination, int flightNumber, String aircraftType, String departureTime, String dayOfWeek) {
        this.destination = destination;
        this.flightNumber = flightNumber;
        this.aircraftType = aircraftType;
        this.departureTime = departureTime;
        this.dayOfWeek = dayOfWeek;
    }

    // Геттери і сеттери для полів

    public String getDestination() {
        return destination;
    }

    public void setDestination(String destination) {
        this.destination = destination;
    }

    public int getFlightNumber() {
        return flightNumber;
    }

    public void setFlightNumber(int flightNumber) {
        this.flightNumber = flightNumber;
    }

    public String getAircraftType() {
        return aircraftType;
    }

    public void setAircraftType(String aircraftType) {
        this.aircraftType = aircraftType;
    }

    public String getDepartureTime() {
        return departureTime;
    }

    public void setDepartureTime(String departureTime) {
        this.departureTime = departureTime;
    }

    public String getDayOfWeek() {
        return dayOfWeek;
    }

    public void setDayOfWeek(String dayOfWeek) {
        this.dayOfWeek = dayOfWeek;
    }

    @Override
    public String toString() {
        return "Flight to " + destination + " (Flight #" + flightNumber + ")" +
                "\nAircraft Type: " + aircraftType +
                "\nDeparture Time: " + departureTime +
                "\nDay of the Week: " + dayOfWeek + "\n";
    }
}

public class Main {
    public static void main(String[] args) {
        // Створюємо масив об'єктів Airline
        ArrayList<Airline> airlines = new ArrayList<>();
        airlines.add(new Airline("New York", 101, "Boeing 737", "08:00", "Monday"));
        airlines.add(new Airline("London", 202, "Airbus A320", "14:30", "Tuesday"));
        airlines.add(new Airline("Paris", 303, "Boeing 747", "10:45", "Wednesday"));
        airlines.add(new Airline("Tokyo", 404, "Boeing 777", "19:15", "Thursday"));
        airlines.add(new Airline("Dubai", 505, "Airbus A380", "16:00", "Friday"));

        // Виводимо список рейсів для заданого пункту призначення
        String destinationToSearch = "London";
        System.out.println("Flights to " + destinationToSearch + ":");
        for (Airline airline : airlines) {
            if (airline.getDestination().equals(destinationToSearch)) {
                System.out.println(airline);
            }
        }

        // Виводимо список рейсів для заданого дня тижня
        String dayOfWeekToSearch = "Tuesday";
        System.out.println("Flights on " + dayOfWeekToSearch + ":");
        for (Airline airline : airlines) {
            if (airline.getDayOfWeek().equals(dayOfWeekToSearch)) {
                System.out.println(airline);
            }
        }

        // Виводимо список рейсів для заданого дня тижня та часу вильоту
        String dayAndTimeToSearch = "Wednesday 10:00";
        System.out.println("Flights on " + dayAndTimeToSearch + " or later:");
        for (Airline airline : airlines) {
            if (airline.getDayOfWeek().equals(dayAndTimeToSearch.split(" ")[0]) &&
                    airline.getDepartureTime().compareTo(dayAndTimeToSearch.split(" ")[1]) >= 0) {
                System.out.println(airline);
            }
        }
    }
}
