

1. **Public Parameters**: A and B exchange $PK_a$ and $PK_b$.
2. **Nonce**: A and B generate nonce $N_a$ and $N_b$.
3. B encrypt $N_b$ => $C_b =f4(PK_b, PK_a, N_b, 0)$:
4. B share $C_b$
5. A and B share $N_a$ and $N_b$
6. A check $C_b =f4(PK_b, PK_a, N_b, 0)$
	1. if fail abort
7. A and B generate PIN $V_a=g2(PK_b, PK_a, N_a, N_b)$
8. USER checks if $V_a=V_b$ 
9. compute LTK




