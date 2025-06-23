Contrário a uma [[Extração de método]]
É importante ressaltar que Inline de Métodos é uma operação mais rara e menos importante do que Extração.

```
private void writeContentToFile(final byte[] revision) { 
	getVirtualFile().setBinaryContent(revision); 
} 

private void write(byte[] revision) { 
	VirtualFile virtualFile = getVirtualFile(); 
	... 
	if (document == null) { 
		writeContentToFile(revision); // única chamada 
	} 
	... 
}
```

-> Método muito pequeno, com uma ou duas linhas de código que é chamado poucas vezes e não garante muitos benefícios com relação ao reuso e incremento de legibilidade do código.

```
private void write(byte[] revision) { 
	VirtualFile virtualFile = getVirtualFile(); 
	... 
	if (document == null) { 
		virtualFile.setBinaryContent(revision); // após inline 
	} 
	... 
}
```