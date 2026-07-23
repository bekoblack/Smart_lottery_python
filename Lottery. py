import random
from datetime import datetime
import os


def save_to_file(winners, all_participants):

    folder = "results"

    if not os.path.exists(folder):
        os.makedirs(folder)

    timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
    filename = f"{folder}/lottery_{timestamp}.txt"

    with open(filename, "w", encoding="utf-8") as f:
        f.write("=== Smart Lottery Result ===\n")
        f.write(f"Date: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}\n")
        f.write(f"Number of participants: {len(all_participants)}\n")
        f.write(f"Number of winners: {len(winners)}\n")
        f.write("-" * 30 + "\n")

        f.write("Participants:\n")
        for p in all_participants:
            f.write(f"- {p}\n")

        f.write("-" * 30 + "\n")

        f.write("Winners:\n")
        for i, w in enumerate(winners, 1):
            f.write(f"{i}. {w}\n")

    print(f"\nResult saved to: {filename}")


def main():

    print("Smart Lottery System v1.0")
    print("Enter the data. Type 'ok' to finish.")
    print("Note: If the first entry is a number, all entries must be numbers.\n")

    participants = []

    first = input("Enter the first entry: ")

    if first.lower() == "ok":
        print("No data entered.")
        return

    if first.isdigit():
        is_number = True
        participants.append(int(first))
    else:
        is_number = False
        participants.append(first)

    while True:

        prompt = "Enter another number: " if is_number else "Enter another name: "
        data = input(prompt)

        if data.lower() == "ok":
            break

        if is_number:

            if data.isdigit():
                participants.append(int(data))
            else:
                print("Error! You started with numbers. Please enter numbers only.")

        else:
            participants.append(data)

    while True:

        try:
            num_winners = int(
                input(f"\nThere are {len(participants)} participants. How many winners? ")
            )

            if 1 <= num_winners <= len(participants):
                break
            else:
                print(f"Enter a number between 1 and {len(participants)}.")

        except ValueError:
            print("Please enter a valid number.")

    winners = random.sample(participants, num_winners)

    print("\nWinners:")

    for i, w in enumerate(winners, 1):
        print(f"{i}. {w}")

    save_choice = input("\nDo you want to save the result to a file? y/n: ")

    if save_choice.lower() == "y":
        save_to_file(winners, participants)

    print("Finished.")


if __name__ == "__main__":
    main()
