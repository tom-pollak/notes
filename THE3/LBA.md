# Linear-bounded automata

> ##### If language L is accepted by some liear-bounded automaton iff L is context-sensitive
> $\therefore$ LBA is type 1 in [[Chomsky hierarchy]]

###### Defined similarly to a [[TM]], except:
- Initial config for input w is **$q0<w>, where <,> ∈ Γ − Σ$**
	- Can also have initial config of $q0<w∆^n>$ (n empty spaces)
-  tape head cannot move to left of < or right of > and <> cannot be overwritten

Unknown whether DLBA is as powerful as NDLBA