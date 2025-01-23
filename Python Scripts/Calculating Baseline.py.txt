def calculate_baseline(samples=30, delay=2):
    total = 0
    for _ in range(samples):
        total += chan.voltage  
        time.sleep(delay)
    return total / samples  


baseline = calculate_baseline()
print(f"Baseline for clean air: {baseline}")
