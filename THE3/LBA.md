# Linear-bounded automata

> ##### If language L is accepted by some liear-bounded automaton iff L is context-sensitive
> $\therefore$ LBA is type 1 in [[Chomsky hierarchy]]

###### Defined similarly to a [[TM]], except:
- Initial config for input w is **$q_0<w>, where <,> \in \Gamma − \Sigma$**
	- Can also have initial config of $q_0<w\Delta^n>$ (n empty spaces)
-  tape head cannot move to left of < or right of > and <> cannot be overwritten

Unknown whether DLBA is as powerful as NDLBA