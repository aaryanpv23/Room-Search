import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {

        Inventory inventory = new Inventory();
        RoomRepository repo = new RoomRepository();

        Room r1 = new Room("1", "Deluxe", 200.0, Arrays.asList("WiFi", "TV"));
        Room r2 = new Room("2", "Suite", 350.0, Arrays.asList("WiFi", "TV", "Mini Bar"));

        repo.addRoom(r1);
        repo.addRoom(r2);

        inventory.setAvailability("1", 2);
        inventory.setAvailability("2", 0);

        // Use RoomCheck instead of SearchService
        RoomCheck roomCheck = new RoomCheck(inventory, repo);
        List<Room> rooms = roomCheck.getAvailableRooms();

        for (Room room : rooms) {
            System.out.println(room.getType() + " - $" + room.getPrice());
        }
    }
}
