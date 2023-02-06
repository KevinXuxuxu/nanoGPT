### Parameter tuning for vmem usage
- Experiment on open web text dataset.
- Data points (n_layer, n_head, n_embd), n_params, (block_size, batch_size) -> stable vmem usage during training
    - (8, 8, 128), 8.08M, (64, 12) -> 1938M
    - (8, 8, 128), 8.08M, (128, 12) -> 2424M
    - (8, 8, 128), 8.08M, (256, 12) -> 3924M
    - (8, 8, 128), 8.08M, (512, 12) -> 6836M (might not reproduce as it approach my gpu limit)
    - (10, 10, 500), 50.32M, (256, 12) -> 5760M
- Initial fitting with therory: x * n_params + y * block_size * batch_size + c = vmem_usage, got 38.865 * n_params + 0.948 * block_size * batch_size + 697.97 = vmem_usage
