# CAC Backend: Contributor's Guide

> This is only for devs.

## Setup instructions for the repo

1. Install `mysql` for your OS. Make sure you add `mysql` to the path variables for the next steps. Create a new user for this project if you wish to do so.
2. Install `node` for your OS. Make sure `npm` comes with your installation, else install that as well.
3. Clone all the 3 repos in the org: `backend`, `user-frontend` and `admin-frontend` (ideally, in a common folder somewhere on your PC for organization and debug support).
4. Each repo has `.env.example` in the root. Copy the file as `.env` for setting up dev credentials.
   The linux command would be `cp .env.example .env` executed in root of each repo.
5. The backend repo has another config file `/config/config.json.example` Copy this file as `/config/config.json`. Update the new file with your mysql creds: lines 4, 5, 8
   The linux command would be `cp config/config.json.example config/config.json` executed in the root of `backend`.

## Database Config

1. In your terminal, login to your sql shell with `mysql -u root -p` or `mysql -u username -p` if you created a new user for the project.
2. Execute the following sql commands to create the database for this project. Note: These are multi-line queries.

   ```sql
   CREATE DATABASE cac
   DEFAULT CHARACTER SET utf8mb4
   DEFAULT COLLATE utf8mb4_unicode_ci;

   USE cac;

   -- Set the timezone to UTC
   SET time_zone = '+00:00';

   -- Set InnoDB as the default storage engine
   SET default_storage_engine=INNODB;
   ```
3. In the rot of `backend`, execute the command `npx sequelize db:migrate`

## Running the project

In each repo root, run `npm run dev` to bring up the dev server. By default the following PORTS are used.

1. Backend: 5000
2. Admin Frontend: 4000
3. User Frontend: 3000
