Created: 2022-03-08 16:35
Status: #idea
Tags:
# Move Semantics
We usually use copy consrtuctors with our classes but most times all we really want to do is to transfer ownership. Copy just wastes time.

#### Move Contructor
- Allows object we'll call $x$ to steal the contents of an object we'll call $y$
- We do not copy. $x$ is not copying the contents of $y$
- Requires that after an object $y$ is moved into an object $x$:
	- $x$ is equal to former value fo $y$
	- $y$ is in *move_from *state which can only
		- Reassign it.
		- Destruct it.

#### Move assignment operator 
- Move constructor what the copy assignemnt operator is to the copy constructor



# References
1.
