import java.util.HashMap;

class UndergroundSystem {

    // Stores check-in information: id -> (stationName, checkInTime)
    class CheckIn {
        String station;
        int time;

        CheckIn(String station, int time) {
            this.station = station;
            this.time = time;
        }
    }

    // Stores total travel time and trip count
    class Trip {
        int totalTime;
        int count;

        Trip() {
            totalTime = 0;
            count = 0;
        }
    }

    private HashMap<Integer, CheckIn> checkInMap;
    private HashMap<String, Trip> tripMap;

    public UndergroundSystem() {
        checkInMap = new HashMap<>();
        tripMap = new HashMap<>();
    }

    public void checkIn(int id, String stationName, int t) {
        checkInMap.put(id, new CheckIn(stationName, t));
    }

    public void checkOut(int id, String stationName, int t) {
        CheckIn checkIn = checkInMap.get(id);

        String route = checkIn.station + "->" + stationName;
        int travelTime = t - checkIn.time;

        Trip trip = tripMap.getOrDefault(route, new Trip());
        trip.totalTime += travelTime;
        trip.count++;

        tripMap.put(route, trip);

        checkInMap.remove(id);
    }

    public double getAverageTime(String startStation, String endStation) {
        String route = startStation + "->" + endStation;
        Trip trip = tripMap.get(route);

        return (double) trip.totalTime / trip.count;
    }
}
