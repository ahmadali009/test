 # Testassignment 

 Testassignment is a direct messaging platform designed for creators, providing enhanced tools, analytics, and organic monetization opportunities.
## Features
- Simplified Communication: Chat with all your followers in one centralized platform
- Analytics & Management Tools: Better manage and group conversations
- Monetization: Built-in monetization features for responding to DMs
- Priority Messages: Customizable fee system for priority messages
- Social Media Integration: Connect multiple social media platforms
- Profile Customization: Personalized welcome messages and creator profiles
## Tech Stack
- Frontend Framework: Next.js 14
- UI Components: Mantine UI
- Styling:
  - Tailwind CSS
  - SCSS
  - PostCSS
- Authentication: NextAuth.js
- Database: Prisma ORM
- Cloud Storage: AWS S3
- Email Services: Resend
- Deployment: Vercel
## Getting Started
### Prerequisites
- Node.js (Latest LTS version recommended)
- npm or yarn
- PostgreSQL database
### Installation
1. Clone the repository:
   git clone https://github.com/yourusername/testassignment.git
   cd testassignment
2. Install dependencies:
   npm install
3. Set up environment variables:
   Create a .env file in the root directory with the following variables:
   DATABASE_URL="your_database_url"
   NEXTAUTH_URL="your_nextauth_url"
   NEXTAUTH_SECRET="your_nextauth_secret"
4. Run database migrations:
   npm run db:migrate:run
### Development
Start the development server:
npm run dev
### Available Scripts
- npm run dev - Start development server
- npm run build - Build production bundle
- npm run start - Start production server
- npm run lint - Run ESLint
- npm run db:migrate:create - Create new database migration
- npm run db:migrate:run - Run database migrations
- npm run db:studio - Open Prisma Studio
- npm run db:seed - Seed database with initial data
## Deployment
The project is configured for deployment on Vercel with GitHub Actions for CI/CD. The staging deployment workflow is triggered on pushes to the main branch.
## Contributing
1. Fork the repository
2. Create your feature branch (git checkout -b feature/AmazingFeature)
3. Commit your changes (git commit -m 'Add some AmazingFeature')
4. Push to the branch (git push origin feature/AmazingFeature)
5. Open a Pull Request
## License
This project is proprietary software. All rights reserved.