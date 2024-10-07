# BlockSniper Game Documentation

## Table of Contents

1. [Introduction](#introduction)
2. [Game Overview](#game-overview)
3. [Game Mechanics](#game-mechanics)
   - [Block Selection](#block-selection)
   - [Bet Placement](#bet-placement)
   - [Winning Criteria](#winning-criteria)
   - [Reward Distribution](#reward-distribution)
4. [Payout Calculation](#payout-calculation)
5. [Fees and Jackpot](#fees-and-jackpot)
6. [Example Gameplay](#example-gameplay)
7. [Preventing Manipulation](#preventing-manipulation)
8. [Game Lifecycle](#game-lifecycle)
9. [Technical Considerations](#technical-considerations)
10. [User Interface](#user-interface)
11. [Additional Features](#additional-features)
12. [Conclusion](#conclusion)

---

## Introduction

BlockSniper is a blockchain-based game where players aim to have their bet transactions included in a specific target block on the Solana blockchain. The closer a player's transaction is included to the target block, the higher their potential rewards. This document outlines the game's rules, mechanics, and development considerations.

## Game Overview

- **Objective**: Get your bet transaction included in the target block or as close as possible before it.
- **Gameplay**: A target block is randomly selected within a specified future range. Players place bets by interacting with the game's smart contract. Rewards are distributed based on proximity to the target block and bet amount.
- **Platform**: Solana blockchain.

## Game Mechanics

### Block Selection

- **Random Selection**: A target block number is randomly generated within a variable range (`min_block` to `max_block`).
- **Future Blocks**: The target block is always set in the future.

### Bet Placement

- **Interaction**: Players place bets by interacting with the game's smart contract.
- **Bet Window**: Bets are accepted up to `x` blocks after the target block. Bets after this window count toward the next round.
- **Bet Amount**: Players can bet any amount.

### Winning Criteria

- **Primary Goal**: Have your bet included in the target block.
- **Proximity Advantage**: If no bets are in the target block, bets before it are considered, with closer bets favored.
- **Missed Bets**: Bets included after the target block (up to `x` blocks later) are missed and added to the pot.

### Reward Distribution

- **Proportional Split**: The pot is split among winners based on proximity and bet size.
- **Negative Profits Possible**: Winners may receive less than their original bet.

## Payout Calculation

For detailed payout calculations, refer to the [Payouts.md](#payoutsmd) document.

### Summary

1. **Calculate Distance to Target Block**.
2. **Compute Proximity Factor**.
3. **Determine Proximity Score**.
4. **Calculate Total Proximity Score**.
5. **Compute Individual Payouts**.
6. **Adjust for Fees**.

## Fees and Jackpot

### Fees

- **Game Fee**: 0.5% of the total pot (variable).
- **Jackpot Fee**: 0.5% of the total pot (variable).
- **Total Fees**: Deducted from the pot before payouts.

### Jackpot Feature

- **Description**: An extra random block, selected like the normal game block but set further in the future.
- **Entry**: Every bet in the normal game counts as an entry to the jackpot.
- **Winning the Jackpot**: If your bet is included in the jackpot block, you win the accumulated jackpot pot.

## Example Gameplay

Refer to the [Payouts.md](#payoutsmd) document for a detailed example.

## Preventing Manipulation

- **Gas Fees**: Offering higher gas fees is allowed.
- **Fair Play**: Transparency ensures fairness.

## Game Lifecycle

- **Round Duration**: From target block selection until `x` blocks after.
- **Continuous Play**: New rounds start automatically.
- **No Player Limit**: Unlimited players per round.

## Technical Considerations

- **Blockchain Platform**: Solana.
- **Smart Contracts**: Utilize Solana's capabilities.
- **Random Number Generation**: Secure methods to prevent manipulation.

## User Interface

- **Web Interface**: For easy interaction and tracking.
- **Direct Contract Interaction**: For advanced users.
- **Mobile Support**: Consider for broader accessibility.

## Additional Features

- **Referral Bonuses**: Incentivize bringing new players.
- **Jackpot**: Additional chance to win big.

## Conclusion

BlockSniper combines strategy and luck, offering a unique blockchain gaming experience. By aiming for precise timing and considering bet sizes, players engage in a challenging and rewarding game.

---

**Next Steps**:

- **Finalize Payout Mechanics**: Implement the payout calculations as per the [Payouts.md](#payoutsmd) document.
- **Implement Fees and Jackpot**: Integrate the fee structure and jackpot mechanism into the smart contract.
- **Develop and Test**: Proceed with coding and rigorous testing.
- **User Education**: Ensure players understand the game mechanics, including the possibility of negative profits.

---

**Note**: For any further details or clarifications, please refer to the attached [Payouts.md](#payoutsmd) document.

---

### Payouts.md

_(The Payouts.md content is included above for reference.)_

# Fees and Jackpot Implementation Details

## Fees

- **Game Fee (Variable)**:

  - Default: **0.5%** of the total pot.
  - Purpose: Covers development and maintenance costs.
- **Jackpot Fee (Variable)**:

  - Default: **0.5%** of the total pot.
  - Purpose: Contributes to the jackpot pot.
- **Total Fees**:

  - Calculated as:
    \[
    \text{Total Fees} = \text{Total Pot} \times (\text{Game Fee} + \text{Jackpot Fee})
    \]
  - Deducted from the total pot before distributing payouts.

## Jackpot Feature

- **Selection of Jackpot Block**:

  - Similar method as the normal target block.
  - Set much further in the future to accumulate a larger pot.
- **Entry to Jackpot**:

  - Every bet in the normal game automatically counts as an entry.
  - No additional action required from players.
- **Winning the Jackpot**:

  - If a player's bet is included in the jackpot block, they win the accumulated jackpot pot.
  - If multiple players have bets in the jackpot block, the jackpot is split proportionally based on bet amounts.
- **Accumulation**:

  - The jackpot pot grows over multiple game rounds until it's won.
  - After a win, the jackpot resets, and accumulation starts anew.

## Example of Fees and Jackpot Contribution

- **Total Pot**: \( 1,000 \)
- **Game Fee (0.5%)**: \( 1,000 \times 0.005 = 5 \)
- **Jackpot Fee (0.5%)**: \( 1,000 \times 0.005 = 5 \)
- **Total Fees**: \( 5 + 5 = 10 \)
- **Adjusted Pot for Payouts**: \( 1,000 - 10 = 990 \)
- **Jackpot Pot**: Increases by \( 5 \)

---

**Reminder**: All percentages are variable and can be adjusted as needed. Transparency with players regarding fees and jackpot contributions is essential for trust and engagement.
