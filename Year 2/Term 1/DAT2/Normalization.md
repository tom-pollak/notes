# Normalization
> #### Producing set of tables with minimal redundancy that support the data requirements of an org

## 1NF
- Each cell should be atomic
- Each table must have a PK

## 2NF
> Only applies to composite key

- Values of each non-PK column determined by every PK part

## 3NF
> **Transitively:** if $a \xrightarrow{determines} b \xrightarrow{determines} c \therefore$ $c$ is transitively dependent on $a$
- Non-PK column is transitively dependent on the PK
	- Occurs when non-PK column is funtionally dependant on a non-PK column