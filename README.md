# Gorkha Baptist Church Management System V3

## Architecture
- Electron Windows desktop application
- SQLite database: `gorkha-baptist-church-v3.db`
- WAL mode and foreign-key support
- Existing membership interface retained
- Core records normalized into separate SQLite tables

## Core tables
members, families, leaders, church_workers, paid_workers, deaths, settings, auth

## V3 expansion tables
attendance, visitors, ministries, ministry_members, events, pastoral_care, assets, finance_transactions, audit_log

The current interface uses the core tables immediately. Expansion tables are already created for future V3 modules and can be connected to new screens without changing the database architecture.

## Run
npm install
npm start

## Build Windows installers
npm run dist

Backups are exported as JSON. The SQLite database remains the authoritative local database.


## Version 3.1 fixes
- Fixed SQLite family ID mapping: `famId` now saves to `families.family_id`.
- Uses native Electron backup export when running as a desktop app.
- Confirmed the login function is separate from member-saving logic in this project.
- Existing JSON restore remains supported and saves restored data back through SQLite.

Before production use, run full add/edit/delete/search/backup/restore testing with sample data.


## Member Transfer Printable Update
- Removed Transfer Letter upload/storage from Member records.
- Transfer Direction, Date, Reason, Church Name, and Transfer Status remain in Member records.
- All remaining transfer fields are included in the printable Member Profile.
- Transfer Letter column removed from Member CSV export.


## Finalized Member Transfer Update
- Transfer Letter removed from Member records and CSV export.
- Printable Member Profile includes Transfer Direction, Transfer Date, Reason, Church Name, and Transfer Status.
- Inline application JavaScript syntax check passed.


## FINAL FIX – Edit Profile Repair
- Removed obsolete mTransferLetter reference that caused Edit Member/Profile to fail after the Transfer Letter field was removed.
- Removed leftover Transfer Letter FileReader/save code.
- Member editing now loads and saves the remaining transfer fields normally.
- JavaScript syntax checks passed for the application and Electron files.
