# Senate Voting System

The **Senate Voting System** is a secure and efficient platform designed to streamline the voting process for the Senate Committee. Developed by the College of Idaho Coding Club, this system ensures transparency, real-time voting, and immediate results while maintaining robust security and data integrity.

[Docs Last Updated: Apr. 8 2025 - Keion Vergara](https://keion.ca)

## Features

- **Secure Login**: Senators can log in with unique credentials, ensuring only authorized users can access the system.
- **Real-Time Voting**: Cast votes in real time with immediate updates to results.
- **Role-Based Access**: Admins can manage users, create sessions, and oversee agendas, while senators can participate in voting.
- **Session Management**: Admins can start and end voting sessions, ensuring votes are only cast during active sessions.
- **Agenda Management**: Admins can create, update, and delete agendas for voting.
- **Voting Results**: View detailed results, including vote counts and final decisions, with visual charts.
- **Auditability**: All session data is recorded and exportable for transparency and accountability.

## Installation

Follow these steps to set up the project:

1. **Install Dependencies**:
   - Ensure you have `Node.js` and `SQLite3` installed on your system.
   - Install project dependencies:
     ```bash
     npm install
     ```

2. **Database Setup**:
   - Delete any existing database file:
     ```bash
     rm senate_voting.db
     ```
   - Set up the database schema:
     ```bash
     sqlite3 senate_voting.db < schema.sql
     sqlite3 senate_voting.db < view.sql
     ```

3. **Run the Application**:
   - Start the server:
     ```bash
     npm start
     ```
   - By default, the application will be hosted at `http://localhost:7777`.

4. **Development Mode** (Optional):
   - Use `nodemon` for automatic server restarts during development:
     ```bash
     npm run dev
     ```

## Usage

### Default Admin Credentials
- **Username**: `secretary`
- **Password**: `changeme123` (hashed in the database)

### Key Functionalities
1. **Admin Dashboard**:
   - Manage users (create, update, delete).
   - Start and end voting sessions.
   - Create and manage agendas.

2. **Senator Dashboard**:
   - View active agendas.
   - Cast votes during active sessions.
   - View voting results.

3. **Voting Process**:
   - Admins create agendas and start a session.
   - Senators log in, view the agenda, and cast their votes.
   - Results are updated in real time and displayed with visual charts.

## Project Structure

```
.
├── .env                 # Environment variables (not included in the repository)
├── .gitignore           # Files and directories to ignore in Git
├── package.json         # Node.js dependencies and scripts
├── schema.sql           # Database schema
├── view.sql             # Database views for roll call and voting results
├── src/
│   ├── app.js           # Main application entry point
│   ├── config/          # Configuration files
│   │   └── database.js  # SQLite database connection
│   ├── controllers/     # Application controllers
│   │   ├── authController.js
│   │   ├── userController.js
│   │   ├── agendaController.js
│   │   └── VoteController.js
│   ├── middleware/      # Middleware for authentication and authorization
│   │   └── auth.js
│   ├── models/          # Database models
│   │   ├── User.js
│   │   ├── Agenda.js
│   │   └── Vote.js
│   ├── public/          # Static assets (CSS, images)
│   │   ├── css/
│   │   │   └── styles.css
│   │   └── images/
│   │       └── senates.png
│   └── views/           # EJS templates for rendering pages
│       ├── dashboard.ejs
│       ├── auth/
│       │   ├── login.ejs
│       │   └── waiting.ejs
│       ├── users/
│       │   ├── agenda.ejs
│       │   ├── manage.ejs
│       │   ├── voting.ejs
│       │   └── vote_result.ejs
│       └── partials/
│           └── navbar.ejs
```

## Security Notes

- **Environment Variables**: Store sensitive information like `SESSION_SECRET` in a `.env` file.
- **HTTPS**: Use an SSL certificate for secure communication in production.
- **Password Hashing**: User passwords are securely hashed using `bcrypt`.

## Development Notes

- **Socket.IO**: Real-time updates for voting results and user approvals are powered by Socket.IO.
- **EJS Templates**: The front-end is rendered using EJS templates for dynamic content.
- **Bootstrap**: The UI is styled with Bootstrap for a responsive and modern design.

## Future Enhancements

- **Two-Factor Authentication**: Add an extra layer of security for user logins.
- **Export Data**: Allow admins to export session and voting data as CSV or PDF.
- **Mobile Optimization**: Improve the UI for better usability on mobile devices.
- **Notifications**: Add email or SMS notifications for session updates and approvals.

## License

This project is licensed under the [MIT License](LICENSE).

## Contributors

- **College of Idaho Coding Club**

For questions or contributions, feel free to open an issue or submit a pull request.
