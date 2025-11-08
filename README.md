#  Mini Blockchain Simulation in Python

This project is a **complete and educational blockchain simulation** written in Python.  
It explains the core ideas of blockchain such as **transactions, blocks, proof of work (mining), rewards, balances, and chain validation**, all in one simple, easy-to-understand script using only Python’s built-in libraries (`hashlib`, `time`).

---

## ⚙️ Overview
The script demonstrates:

- Creating transactions between users  
- Grouping transactions into blocks  
- Mining blocks using **Proof of Work**  
- Rewarding the miner for validating blocks  
- Calculating user balances  
- Verifying blockchain integrity  

---

## Full Step-by-Step Explanation

```python
# Step 1 – Create Transactions
my_coin = Blockchain()
my_coin.create_transaction(Transactions("Alice", "Bob", 50))
my_coin.create_transaction(Transactions("Bob", "Charlie", 25))

# ➡ These two transactions are added to the pending transactions list, not yet written to the blockchain.
# They will be recorded in the next mined block.

# Step 2 – Mine Pending Transactions
my_coin.mine_pending_transactions("miner1")
print("Solde du mineur :", my_coin.get_balance_of_address("miner1"))

# ➡ A new block is created containing all pending transactions.
# It is mined (Proof of Work – the hash must start with "00") and added to the blockchain.
# Then, a reward transaction is created for miner1, but it remains pending for the next block.
# → Miner balance = 0 (reward not yet recorded).

# Example Output:
# Bloc miné ! Nonce = 346, Hash = 00af12b...
# Bloc validé et ajouté à la chaîne.
# Solde du mineur : 0


# Step 3 – Mine Again to Receive the Reward
my_coin.mine_pending_transactions("miner1")
print("Solde du mineur :", my_coin.get_balance_of_address("miner1"))

# ➡ The second block includes the previous pending reward.
# Once mined, miner1 officially earns 10 units.
# A new reward transaction (10 units) is generated again for the next block.
# → Miner balance = 10.

# Example Output:
# Bloc miné ! Nonce = 215, Hash = 00b2c8fa...
# Bloc validé et ajouté à la chaîne.
# Solde du mineur : 10


# Step 4 – Verify Blockchain Integrity
print("Blockchain valide ?", my_coin.is_chain_valid())

# ➡ The blockchain is verified: each block’s hash and its link to the previous block must match.
# If no tampering occurred → Blockchain valide ? True

# Example Output:
# Blockchain valide ? True
