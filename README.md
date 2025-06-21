# MyHisaab Lead Management System

A comprehensive lead management dashboard for MyHisaab.com with coupon management and agent assignment features.

## Features

- **Lead Management**: Capture, track, and manage customer leads
- **Coupon System**: Create and validate discount coupons
- **Agent Assignment**: Assign leads to agents automatically or manually
- **Dashboard Analytics**: Overview of leads, agents, and coupon performance
- **Secure Authentication**: Admin login with JWT tokens

## Setup Instructions

### 1. Environment Configuration

1. Copy `.env.example` to `.env`
2. Update the Xano configuration:
   ```
   VITE_XANO_BASE_URL=https://your-xano-instance.com/api:v1
   VITE_XANO_API_KEY=your-api-key-here
   ```

### 2. Xano Backend Setup

Create the following endpoints in your Xano instance:

#### Authentication
- `POST /auth/login` - Admin login

#### Leads
- `GET /leads` - Get all leads
- `POST /leads` - Create new lead
- `PATCH /leads/{id}` - Update lead status
- `PATCH /leads/{id}/assign` - Assign lead to agent

#### Agents
- `GET /agents` - Get all agents
- `POST /agents` - Create new agent

#### Coupons
- `GET /coupons` - Get all coupons
- `POST /coupons` - Create new coupon
- `GET /coupons/validate/{code}` - Validate coupon
- `PATCH /coupons/{id}` - Update coupon
- `DELETE /coupons/{id}` - Delete coupon

### 3. Deployment Options

#### Option A: Subdomain (Recommended)
Deploy to `admin.myhisaab.com` for easy access

#### Option B: Directory
Deploy to `myhisaab.com/admin/`

#### Option C: Embed Widget
Integrate specific components into existing pages

### 4. Integration with Main Website

Add this form to your main website to capture leads:

```html
<form action="https://your-xano-instance.com/api:v1/leads" method="POST">
  <input type="text" name="name" placeholder="Full Name" required>
  <input type="email" name="email" placeholder="Email" required>
  <input type="tel" name="phone" placeholder="Phone" required>
  <textarea name="message" placeholder="Message" required></textarea>
  <input type="text" name="couponCode" placeholder="Coupon Code (Optional)">
  <button type="submit">Submit</button>
</form>
```

## API Endpoints

All endpoints require authentication via Bearer token in the Authorization header.

### Lead Endpoints
- `GET /leads` - Returns array of leads
- `POST /leads` - Creates new lead
- `PATCH /leads/{id}` - Updates lead
- `PATCH /leads/{id}/assign` - Assigns lead to agent

### Coupon Endpoints
- `GET /coupons` - Returns array of coupons
- `POST /coupons` - Creates new coupon
- `GET /coupons/validate/{code}` - Validates coupon code

### Agent Endpoints
- `GET /agents` - Returns array of agents
- `POST /agents` - Creates new agent

## Security

- All API calls are authenticated
- Admin access requires login
- Tokens are stored securely in localStorage
- CORS configured for your domain

## Support

For technical support, contact the development team.