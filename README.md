# agri-project
agriculture based program
def suggest_crop(soil, temp, rainfall, ph):
    
    soil = soil.lower()
    
    # Rules for different crops
    crops = {
        "Rice":      {"soil": "clay", "temp": (25, 35), "rainfall": (1000, 2000), "ph": (5.5, 7)},
        "Wheat":     {"soil": "loamy", "temp": (15, 25), "rainfall": (500, 1000), "ph": (6, 7.5)},
        "Cotton":    {"soil": "sandy", "temp": (21, 30), "rainfall": (700, 1300), "ph": (5, 6.5)},
        "Sugarcane": {"soil": "clay", "temp": (20, 38), "rainfall": (1500, 2500), "ph": (6.5, 7.5)}
    }

    suitable_crops = []

    for crop, conditions in crops.items():
        if (soil == conditions["soil"] and
            conditions["temp"][0] <= temp <= conditions["temp"][1] and
            conditions["rainfall"][0] <= rainfall <= conditions["rainfall"][1] and
            conditions["ph"][0] <= ph <= conditions["ph"][1]):
            suitable_crops.append(crop)

    return suitable_crops


def main():
    print("=== Smart Crop Suggestion System ===")

    while True:
        print("\nEnter your field conditions:")

        soil = input("Soil type (clay/sandy/loamy): ")
        try:
            temp = float(input("Temperature (°C): "))
            rainfall = float(input("Rainfall (mm): "))
            ph = float(input("Soil pH (e.g., 6.5): "))
        except ValueError:
            print("Invalid input! Please enter numeric values for temperature, rainfall, and pH.")
            continue

        crops = suggest_crop(soil, temp, rainfall, ph)

        if crops:
            print("\n✅ Suitable crop(s) for your land:")
            for crop in crops:
                print(f"- {crop}")
        else:
            print("\n❌ No suitable crops found based on the input conditions.")

        again = input("\nDo you want to try again? (yes/no): ").lower()
        if again != 'yes':
            print("Thank you for using the Smart Crop Suggestion System!")
            break


if _name_ == "_main_":
main()
