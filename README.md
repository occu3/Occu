import hashlib
import time

def mine_block(difficulty):
    prefix_str = '0' * difficulty
    nonce = 0
    start_time = time.time()

    while True:
        text = f"block-data-{nonce}"
        hash_result = hashlib.sha256(text.encode()).hexdigest()

        if hash_result.startswith(prefix_str):
            end_time = time.time()
            print(f"🎉 Block mined!")
            print(f"Nonce: {nonce}")
            print(f"Hash: {hash_result}")
            print(f"Time taken: {end_time - start_time:.2f} seconds")
            break
        else:
            nonce += 1

# Difficulty 4 means the hash must start with 4 zeros
mine_block(difficulty=4)
