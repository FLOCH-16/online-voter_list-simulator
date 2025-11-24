# online-voter_list-simulator
The simple online voting system Python code is designed to offer a basic digital voting platform without AI or complex infrastructure. Here is a detailed description of its design and functionality

#CODE OF THE PROGRAM
# Simple Online Voting System (No AI)

# Dictionary to store registered voters: voter_id -> has_voted (True/False)
registered_voters = {}

# Dictionary to store candidates and vote counts
candidates = {
    "Alice": 0,
    "Bob": 0,
    "Charlie": 0,
}

def register_voter(voter_id):
    if voter_id in registered_voters:
        print("Voter already registered.")
    else:
        registered_voters[voter_id] = False
        print("Voter registered successfully.")

def cast_vote(voter_id, candidate):
    if voter_id not in registered_voters:
        print("Voter not registered.")
        return
    if registered_voters[voter_id]:
        print("You have already voted.")
        return
    if candidate not in candidates:
        print("Invalid candidate.")
        return
     candidates[candidate] += 1
    registered_voters[voter_id] = True
    print(f"Vote cast successfully for {candidate}.")

def show_results():
    print("\nVoting Results:")
    for candidate, votes in candidates.items():
        print(f"{candidate}: {votes} votes")

def main():
    print("Welcome to the Simple Online Voting System")
    while True:
        print("\nMenu Options:")
        print("1. Register Voter")
        print("2. Cast Vote")
        print("3. Show Results")
        print("4. Exit")

        choice = input("Select an option (1-4): ").strip()

        if choice == '1':
            voter_id = input("Enter Voter ID: ").strip()
            register_voter(voter_id)
        elif choice == '2':
            voter_id = input("Enter Voter ID: ").strip()
            print("Candidates:", ', '.join(candidates.keys()))
            candidate = input("Enter Candidate Name: ").strip()
            cast_vote(voter_id, candidate)
        elif choice == '3':
            show_results()
        elif choice == '4':
            print("Exiting voting system.")
            break
        else:
            print("Invalid option, please try again.")

if __name__ == "__main__":
    main()
