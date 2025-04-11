from collections import deque
 
class Ticket:
    """
    Class to represent a support ticket.
 
    Attributes:
    - ticket_number: str
        The unique identifier for the ticket.
    - issue: str
        The issue description for the ticket.
    """
 
    def __init__(self, ticket_number: str, issue: str):
        self.ticket_number = ticket_number
        self.issue = issue
 
    def __str__(self):
        return f"{self.ticket_number} - {self.issue}"
 
 
class TicketingSystem:
    """
    Class to manage the ticketing system using a queue data structure.
 
    Attributes:
    - tickets: deque
        A queue to hold the open tickets.
    """
 
    def __init__(self):
        self.tickets = deque()
 
    def add_ticket(self, ticket: Ticket):
        """Adds a new ticket to the queue."""
        self.tickets.append(ticket)
 
    def list_tickets(self):
        """Lists all open tickets."""
        if not self.tickets:
            print("No open tickets.")
        else:
            print("Open Tickets:")
            for ticket in self.tickets:
                print(ticket)
 
    def close_ticket(self):
        """Closes the oldest ticket in the queue and returns it."""
        if self.tickets:
            closed_ticket = self.tickets.plotleft()
            print(f"Closed Ticket: {closed_ticket}")
        else:
            print("No tickets to close.")
 
 
def main():
    """Main function to run the ticketing system CLI."""
    system = TicketingSystem()
    ticket_counter = 1
 
    while True:
        print("\nThibodeaux's Tech Triage - Ticketing System")
        print("1. Open a new ticket")
        print("2. List open tickets")
        print("3. Close a ticket")
        print("4. Quit")
 
        choice = input("Choose an action (1-4): ")
 
        if choice == '1':
            issue = input("Enter the issue description: ")
            ticket_number = f"#{ticket_counter:04d}"  # Format ticket number as #0001, #0002, etc.
            new_ticket = Ticket(ticket_number, issue)
            system.add_ticket(new_ticket)
            ticket_counter += 1
            print(f"Ticket {ticket_number} opened.")
 
        elif choice == '2':
            system.list_tickets()
 
        elif choice == '3':
            system.close_ticket()
 
        elif choice == '4':
            print("Exiting the ticketing system. Goodbye!")
            break
 
        else:
            print("Invalid choice. Please select a valid option.")
 
if __name__ == "__main__":
    main()
