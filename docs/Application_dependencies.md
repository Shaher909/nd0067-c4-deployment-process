# Application Dependencies

## Node.js Version

- **Node.js**: 14.15.0
- **NPM**: 6.14+

## Backend (API) Dependencies

### Runtime Dependencies

- **express**: Web framework for Node.js
- **sequelize**: ORM for PostgreSQL database
- **pg**: PostgreSQL client
- **aws-sdk**: AWS services integration (S3)
- **cors**: Cross-Origin Resource Sharing middleware
- **bcryptjs**: Password hashing
- **jsonwebtoken**: JWT authentication
- **body-parser**: Request body parsing
- **dotenv**: Environment variable management

### Development Dependencies

- **typescript**: TypeScript compiler
- **@types/\***: TypeScript type definitions
- **ts-node-dev**: Development server with hot reload

## Frontend Dependencies

### Runtime Dependencies

- **@angular/core**: Angular framework (v8.2.14)
- **@ionic/angular**: Ionic UI components (v4.1.0)
- **rxjs**: Reactive programming library
- **zone.js**: Angular change detection

### Development Dependencies

- **@angular/cli**: Angular CLI for building
- **@angular/compiler-cli**: Angular compiler
- **typescript**: TypeScript compiler

## AWS Services Required

- **S3**: Static website hosting and media storage
- **Elastic Beanstalk**: API hosting
- **RDS**: PostgreSQL database

## CI/CD Dependencies

- **CircleCI Orbs**:
  - `node@5.0.2`: Node.js setup
  - `aws-cli@3.1.1`: AWS CLI
  - `aws-elastic-beanstalk@2.0.1`: EB CLI
