# RPS

<img width="680" height="393" alt="image" src="https://github.com/user-attachments/assets/acdf814f-ed6e-4fa6-8f0a-da444ae8bf80" />

# Rock–Paper–Scissors (RPS) with RNN Prediction

An interactive Rock–Paper–Scissors game where the **player inputs moves via hand gestures**, and **predicts the player’s next move** from historical sequences using a **Recurrent Neural Network (RNN)**.

## Overview
This project combines:
- **Computer Vision**: hand gesture recognition (Rock/Paper/Scissors)
- **Sequence Modeling**: RNN-based prediction from move history
- **Game Logic**: round-based scoring and state transitions

## Game Rules & State
- Each round produces one of: **Player wins (+1)**, **AI wins (+1)**, or **Tie (+0)**.
- The game flow is modeled as states: **Start → Battle (Player vs AI) → Stop/Exit**.
- Each round ends when the **timer exceeds ~3 seconds**.

## Proposed Method
1. **Dataset**
2. **Data Processing**
3. **Hand Detection (Computer Vision)**
4. **RNN (Prediction Model)**
5. **Model Evaluation**

## Dataset
Source: **Roshambo.me**  
Scale: **~150,000 human games**  
Fields used:
- `game_id`
- `game_round_id`
- `player_one_throw`
- `player_two_throw`

## Data Processing (High-level)
- Read and process original game logs
- Generate simulated data (to enrich sequences)
- One-hot encode moves
- Prepare training sequences
- Split dataset (with shuffling buffer)
  - test set: 2,000 samples
  - validation set: 2,000 samples
  - remaining for training

## Hand Gesture Input (Computer Vision)
Hand tracking is implemented using **cvzone** (Hand Tracking Module) with **21-point hand landmark identification**.  
The detected gesture is mapped to one of: Rock / Paper / Scissors for gameplay input.

## Prediction Model (RNN)
We use an **RNN** to learn dependencies in sequences of moves and predict the player’s next action from history.

## Results
Model evaluation on the test set:
- **Test Accuracy:** 95.46%
- **Test Loss:** 0.0759  
Training/validation behavior indicates the model generalizes well (no clear overfitting observed).
