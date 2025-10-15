# AdvanceDAO - Salary Advance DAO

## Overview

AdvanceDAO is a decentralized autonomous organization (DAO) that provides short-term employee financing through salary advances. The system allows verified employees to request advance payments against their future salary, with community governance deciding on approvals and system parameters.

## System Architecture

The AdvanceDAO consists of two main smart contracts:

### 1. Advance Pool Contract (`advance-pool.clar`)
- **Core Functions**: Handles advance requests, approvals, and repayments
- **Pool Management**: Manages the funding pool contributed by employers and investors
- **Employee Verification**: Tracks verified employees and their salary information
- **Advance Lifecycle**: Processes the complete lifecycle from request to repayment

### 2. Governance Contract (`dao-governance.clar`)
- **Voting System**: Implements DAO voting for advance approvals
- **Parameter Management**: Controls system parameters like interest rates and limits
- **Proposal System**: Manages proposals for system changes
- **Member Management**: Handles DAO membership and voting power

## Key Features

### Employee Verification System
- Employees must be verified by their employers
- Salary information is recorded for advance calculations
- Employment status tracking ensures eligible participants

### Advance Request Process
1. **Request Submission**: Verified employees submit advance requests
2. **DAO Voting**: Community votes on approval within voting period
3. **Automatic Processing**: Approved requests are processed automatically
4. **Repayment Tracking**: System tracks repayment schedules and deadlines

### Governance Features
- **Democratic Voting**: All DAO members participate in decision-making
- **Proposal System**: Members can propose system changes
- **Parameter Control**: Community controls interest rates, advance limits
- **Treasury Management**: Decentralized control of funding pool

## Technical Specifications

### Advance Pool Contract Features
- **Pool Contributions**: Employers and investors can contribute to the funding pool
- **Employee Management**: Add/remove verified employees with salary data
- **Advance Processing**: Request, approve, disburse, and track advances
- **Repayment System**: Automated repayment tracking and processing
- **Interest Calculation**: Configurable interest rates on advances

### Governance Contract Features
- **Membership System**: DAO members with voting power based on contributions
- **Voting Mechanism**: Proposal-based voting with time limits
- **Parameter Updates**: Community-controlled system configuration
- **Treasury Operations**: Decentralized fund management

## Contract Functions

### Advance Pool (`advance-pool.clar`)
- `contribute-to-pool(amount)` - Add funds to the advance pool
- `add-employee(employee, monthly-salary, employer)` - Verify new employee
- `request-advance(amount, repayment-blocks)` - Submit advance request
- `approve-advance(request-id)` - Approve advance request (DAO only)
- `repay-advance(request-id, amount)` - Make repayment on advance
- `withdraw-from-pool(amount)` - Withdraw contributed funds (with restrictions)

### DAO Governance (`dao-governance.clar`)
- `join-dao(contribution)` - Become DAO member with STX contribution
- `create-proposal(proposal-type, target, new-value)` - Create governance proposal
- `vote-on-proposal(proposal-id, support)` - Vote on active proposal
- `execute-proposal(proposal-id)` - Execute approved proposal
- `vote-on-advance(request-id, support)` - Vote on advance request

## Security Features

1. **Access Control**: Only verified employees can request advances
2. **Voting Requirements**: Advances require DAO approval
3. **Fund Protection**: Pool withdrawals have safety restrictions
4. **Parameter Limits**: Governance controls prevent extreme changes
5. **Repayment Enforcement**: Automatic tracking and penalties

## Usage Flow

### For Employees
1. Get verified by employer through `add-employee`
2. Request advance using `request-advance`
3. Wait for DAO voting period and approval
4. Receive advance if approved
5. Repay according to schedule using `repay-advance`

### For Employers/Investors
1. Contribute to pool using `contribute-to-pool`
2. Join DAO with `join-dao` for voting rights
3. Verify employees with `add-employee`
4. Participate in governance through voting

### For DAO Members
1. Vote on advance requests using `vote-on-advance`
2. Create proposals for system changes
3. Vote on governance proposals
4. Help maintain system parameters

## Contract Configuration

- **Maximum Advance**: 50% of monthly salary or 10,000 μSTX
- **Interest Rate**: 5% (DAO configurable)
- **Voting Period**: 144 blocks (~24 hours)
- **Quorum Requirement**: 30% of DAO members
- **Repayment Period**: Up to 2016 blocks (~2 weeks)

## Development

### Prerequisites
- Clarinet CLI
- Node.js for testing
- STX wallet for deployment

### Setup
```bash
# Clone and setup
cd AdvanceDAO
clarinet check          # Verify contracts
clarinet test           # Run test suite
```

### Testing
The project includes comprehensive tests for both contracts covering:
- Employee verification and management
- Advance request and approval workflow
- Repayment processing and tracking
- DAO governance and voting
- Edge cases and error conditions

## Deployment

The contracts are designed to be deployed on the Stacks blockchain with proper initialization of system parameters and initial DAO membership.

## Security Considerations

- All state changes are properly validated
- Fund transfers include safety checks
- Voting mechanisms prevent manipulation
- Employee verification ensures legitimate requests
- Repayment enforcement protects lenders

## License

This project is open source and available under standard licensing terms.
