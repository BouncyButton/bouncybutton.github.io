$$
\begin{algorithm}
\caption{LearnOneRule}
\begin{algorithmic}[1]
\STATE \textbf{Input:} 
\STATE $c_i$: a class value
\STATE $P_i$: a set of positive examples for class $c_i$
\STATE $N_i$: a set of negative examples for class $c_i$
\STATE $F$: a set of features
\STATE \textbf{Algorithm:}
\STATE $r := (c_i \leftarrow B)$, where $B \leftarrow \emptyset$
\STATE \textbf{repeat}
\STATE \hspace{1em} build refinements $\rho(r) \leftarrow \{r \mid r = (c_i \leftarrow B \land f)\}$ for all $f \in F$
\STATE \hspace{1em} evaluate all $r \in \rho(r)$ according to a quality criterion
\STATE \hspace{1em} $r :=$ the best refinement $r$ in $\rho(r)$
\STATE \textbf{until} $r$ satisfies a quality threshold or covers no examples from $N_i$
\STATE \textbf{Output:} learned rule $r$
\end{algorithmic}
\end{algorithm}
$$