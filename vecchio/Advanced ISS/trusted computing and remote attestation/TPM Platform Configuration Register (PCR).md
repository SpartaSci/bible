

The TPM can report the current state of the system. To store the current state and to report it, the TPM contains a special set of registers named PCR. They are registers that keep the history of the platform configuration. The set of PCRs is the core mechanism for recording platform integrity. These registers are reset only at platform reset (after a reboot or after a hardware signal). Reset means that all the registers will start with 0. This is important because even if malicious code infected the system, it cannot have the registers back to some value.

These registers have only two operations: one is the reset, the second one is extend. The extend operation is:

$$
PCR_{new} = hash(PCR_{old} || digest\_of\_new\_data)
$$

The old value contained in the PCR, concatenated to the digest of some new data, is hashed. The result becomes the new value of the PCR. This is the only operation that can be performed. This operation is designed for trusted computing.

The value of the PCR can be used to gate (to control) access to other TPM objects. For example, in Windows, BitLocker can be activated, that is disk encryption. To activate it, TPM must be enabled, because BitLocker is sealing the disk encryption key to PCR values. It means that the key needed to decrypt the disk is available only when Windows is booted, and it has not been modified. If BitLocker is activated, the key is stored inside the TPM and if the system is not in a specific state, and the state is not coincident with the STATE of values present in the PCR, the decryption will not work (binding + sealing).
