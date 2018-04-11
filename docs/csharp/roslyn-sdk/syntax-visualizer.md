---
title: Explorar código com o visualizador de sintaxe Roslyn no Visual Studio
description: O visualizador de sintaxe fornece uma ferramenta visual para explorar os modelos que o SDK do .NET Compiler Platform gera para o código.
author: billwagner
ms.author: wiwagn
ms.date: 03/07/2018
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: ec9d9fcdcaf2c018762542f6dc403e2a4f89376b
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a><span data-ttu-id="2e028-103">Explorar código com o visualizador de sintaxe Roslyn no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2e028-103">Explore code with the Roslyn syntax visualizer in Visual Studio</span></span>

<span data-ttu-id="2e028-104">Este artigo oferece uma visão geral sobre a ferramenta de Visualizador de sintaxe que é fornecida como parte do SDK do .NET Compiler Platform ("Roslyn").</span><span class="sxs-lookup"><span data-stu-id="2e028-104">This article provides an overview of the Syntax Visualizer tool that ships as part of the .NET Compiler Platform ("Roslyn") SDK.</span></span> <span data-ttu-id="2e028-105">O Visualizador de sintaxe é uma janela de ferramentas que ajuda a inspecionar e explorar árvores de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="2e028-105">The Syntax Visualizer is a tool window that helps you inspect and explore syntax trees.</span></span> <span data-ttu-id="2e028-106">É uma ferramenta essencial para compreender os modelos do código que você deseja analisar.</span><span class="sxs-lookup"><span data-stu-id="2e028-106">It's an essential tool to understand the models for code you want to analyze.</span></span> <span data-ttu-id="2e028-107">Também é um auxílio para depuração ao desenvolver seus próprios aplicativos usando o SDK do.NET Compiler Platform ("Roslyn").</span><span class="sxs-lookup"><span data-stu-id="2e028-107">It's also a debugging aid when you develop your own applications using the .NET Compiler Platform (“Roslyn”) SDK.</span></span> <span data-ttu-id="2e028-108">Abra essa ferramenta ao criar seus primeiros analisadores.</span><span class="sxs-lookup"><span data-stu-id="2e028-108">Open this tool as you create your first analyzers.</span></span> <span data-ttu-id="2e028-109">O visualizador ajuda você a entender os modelos usados pelas APIs.</span><span class="sxs-lookup"><span data-stu-id="2e028-109">The visualizer helps you understand the models used by the APIs.</span></span> <span data-ttu-id="2e028-110">Você também pode usar ferramentas como [SharpLab](https://sharplab.io) ou [LINQPad](https://www.linqpad.net/) para inspecionar o código e entender as árvores de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="2e028-110">You can also use tools like [SharpLab](https://sharplab.io) or [LINQPad](https://www.linqpad.net/) to inspect code and understand syntax trees.</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="2e028-111">Familiarize-se com os conceitos usados no SDK do.NET Compiler Platform lendo o artigo de [visão geral](compiler-api-model.md).</span><span class="sxs-lookup"><span data-stu-id="2e028-111">Familiarize yourself with the concepts used in the .NET Compiler Platform SDK by reading the [overview](compiler-api-model.md) article.</span></span> <span data-ttu-id="2e028-112">Ele fornece uma introdução a árvores de sintaxe, nós, tokens e trívia.</span><span class="sxs-lookup"><span data-stu-id="2e028-112">It provides an introduction to syntax trees, nodes, tokens, and trivia.</span></span>

## <a name="syntax-visualizer"></a><span data-ttu-id="2e028-113">Visualizador de sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e028-113">Syntax Visualizer</span></span>

<span data-ttu-id="2e028-114">O **Visualizador de sintaxe** permite a inspeção da árvore de sintaxe de arquivo de código C# ou VB na janela do editor atualmente ativa dentro do IDE do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2e028-114">The **Syntax Visualizer** enables inspection of the syntax tree for the C# or VB code file in the current active editor window inside the Visual Studio IDE.</span></span> <span data-ttu-id="2e028-115">O visualizador pode ser iniciado ao clicar em **Exibir** > **Outras Janelas** > **Visualizador de sintaxe**.</span><span class="sxs-lookup"><span data-stu-id="2e028-115">The visualizer can be launched by clicking on **View** > **Other Windows** > **Syntax Visualizer**.</span></span>  <span data-ttu-id="2e028-116">Você também pode usar a barra de ferramentas de **Início Rápido** no canto superior direito.</span><span class="sxs-lookup"><span data-stu-id="2e028-116">You can also use the **Quick Launch** toolbar in the upper right corner.</span></span> <span data-ttu-id="2e028-117">Digite "sintaxe" e o comando para abrir o **Visualizador de sintaxe** deverá aparecer.</span><span class="sxs-lookup"><span data-stu-id="2e028-117">Type "syntax", and the command to open the **Syntax Visualizer** should appear.</span></span>

<span data-ttu-id="2e028-118">Este comando abre o Visualizador de sintaxe como uma janela de ferramentas flutuante.</span><span class="sxs-lookup"><span data-stu-id="2e028-118">This command opens the Syntax Visualizer as a floating tool window.</span></span> <span data-ttu-id="2e028-119">Se você não tiver uma janela de editor de código aberta, a exibição ficará em branco, conforme mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e028-119">If you don't have a code editor window open, the display is blank, as shown in the following figure.</span></span> 

![A janela de ferramentas do Visualizador de sintaxe](media/syntax-visualizer.png)

<span data-ttu-id="2e028-121">Encaixe esta janela de ferramentas em um local conveniente dentro do Visual Studio, como o lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="2e028-121">Dock this tool window at a convenient location inside Visual Studio, such as the left side.</span></span> <span data-ttu-id="2e028-122">O Visualizador mostra informações sobre o arquivo de código atual.</span><span class="sxs-lookup"><span data-stu-id="2e028-122">The Visualizer shows information about the current code file.</span></span>

<span data-ttu-id="2e028-123">Crie um novo projeto usando o comando **Arquivo** > **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="2e028-123">Create a new project using the **File** > **New Project** command.</span></span> <span data-ttu-id="2e028-124">Você pode criar um projeto do VB ou C#.</span><span class="sxs-lookup"><span data-stu-id="2e028-124">You can create either a VB or C# project.</span></span> <span data-ttu-id="2e028-125">Quando o Visual Studio abre o arquivo de código principal deste projeto, o visualizador exibe a árvore de sintaxe dele.</span><span class="sxs-lookup"><span data-stu-id="2e028-125">When Visual Studio opens the main code file for this project, the visualizer displays the syntax tree for it.</span></span> <span data-ttu-id="2e028-126">Você pode abrir qualquer arquivo de C# ou VB existente nesta instância do Visual Studio e o visualizador exibirá a árvore de sintaxe do arquivo correspondente.</span><span class="sxs-lookup"><span data-stu-id="2e028-126">You can open any existing C# / VB file in this Visual Studio instance, and the visualizer displays that file's syntax tree.</span></span> <span data-ttu-id="2e028-127">Se você tiver vários arquivos de código abertos no Visual Studio, o visualizador exibirá a árvore de sintaxe do arquivo de código atualmente ativo, (o arquivo de código que tem o foco do teclado).</span><span class="sxs-lookup"><span data-stu-id="2e028-127">If you have multiple code files open inside Visual Studio, the visualizer displays the syntax tree for the currently active code file, (the code file that has keyboard focus.)</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="2e028-128">C#</span><span class="sxs-lookup"><span data-stu-id="2e028-128">C#</span></span>](#tab/csharp)
![Visualizando uma árvore de sintaxe de C#](media/visualize-csharp.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="2e028-130">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e028-130">Visual Basic</span></span>](#tab/visual-basic)
<a name="visualizing-a-vb-syntax-treemediavisualize-visual-basicpng"></a>![Visualizando uma árvore de sintaxe do VB](media/visualize-visual-basic.png)
---

<span data-ttu-id="2e028-132">Conforme mostrado nas imagens acima, a janela de ferramentas do visualizador exibe a árvore de sintaxe na parte superior e uma grade de propriedade na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="2e028-132">As shown in the preceding images, the visualizer tool window displays the syntax tree at the top and a property grid at the bottom.</span></span> <span data-ttu-id="2e028-133">A grade de propriedade exibe as propriedades do item atualmente selecionado na árvore, incluindo *Type* e *Kind* (SyntaxKind) do .NET do item.</span><span class="sxs-lookup"><span data-stu-id="2e028-133">The property grid displays the properties of the item that is currently selected in the tree, including the .NET *Type* and the *Kind* (SyntaxKind) of the item.</span></span>

<span data-ttu-id="2e028-134">As árvores de sintaxe incluem três tipos de itens: *nós*, *tokens* e *trívia*.</span><span class="sxs-lookup"><span data-stu-id="2e028-134">Syntax trees comprise three types of items – *nodes*, *tokens*, and *trivia*.</span></span> <span data-ttu-id="2e028-135">Você pode ler mais sobre esses tipos no artigo [Trabalhar com sintaxe](work-with-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="2e028-135">You can read more about these types in the [Work with syntax](work-with-syntax.md) article.</span></span> <span data-ttu-id="2e028-136">Os itens de cada tipo estão representados com cores diferentes.</span><span class="sxs-lookup"><span data-stu-id="2e028-136">Items of each type are represented using a different color.</span></span> <span data-ttu-id="2e028-137">Clique no botão "Legenda" para uma visão geral das cores usadas.</span><span class="sxs-lookup"><span data-stu-id="2e028-137">Click on the ‘Legend’ button for an overview of the colors used.</span></span>

<span data-ttu-id="2e028-138">Cada item da árvore também exibe sua própria **extensão**.</span><span class="sxs-lookup"><span data-stu-id="2e028-138">Each item in the tree also displays its own **span**.</span></span> <span data-ttu-id="2e028-139">A **extensão** é composta pelos índices (a posição inicial e final) do nó no arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="2e028-139">The **span** is the indices (the starting and ending position) of that node in the text file.</span></span>  <span data-ttu-id="2e028-140">No exemplo de C# anterior, o token “UsingKeyword [0..5)” selecionado tem uma **abrangência** de cinco caracteres de largura, [0..5).</span><span class="sxs-lookup"><span data-stu-id="2e028-140">In the preceding C# example, the selected “UsingKeyword [0..5)” token has a **Span** that is five characters wide, [0..5).</span></span> <span data-ttu-id="2e028-141">A notação "[..)" significa que o índice inicial faz parte da extensão, mas o índice final não.</span><span class="sxs-lookup"><span data-stu-id="2e028-141">The "[..)" notation means that the starting index is part of the span, but the ending index is not.</span></span>

<span data-ttu-id="2e028-142">Há duas maneiras de navegar na árvore:</span><span class="sxs-lookup"><span data-stu-id="2e028-142">There are two ways to navigate the tree:</span></span>
* <span data-ttu-id="2e028-143">Expandir ou clicar em itens na árvore.</span><span class="sxs-lookup"><span data-stu-id="2e028-143">Expand or click on items in the tree.</span></span> <span data-ttu-id="2e028-144">O visualizador seleciona automaticamente o texto correspondente à extensão do item no editor de código.</span><span class="sxs-lookup"><span data-stu-id="2e028-144">The visualizer automatically selects the text corresponding to this item’s span in the code editor.</span></span>
* <span data-ttu-id="2e028-145">Clicar ou selecionar texto no editor de código.</span><span class="sxs-lookup"><span data-stu-id="2e028-145">Click or select text in the code editor.</span></span> <span data-ttu-id="2e028-146">No exemplo anterior do VB, se você seleciona a linha que contém "Module Module1" no editor de código, o visualizador navega automaticamente até o nó ModuleStatement correspondente na árvore.</span><span class="sxs-lookup"><span data-stu-id="2e028-146">In the preceding VB example, if you select the line containing "Module Module1" in the code editor, the visualizer automatically navigates to the corresponding ModuleStatement node in the tree.</span></span> 

<span data-ttu-id="2e028-147">O visualizador realça o item da árvore cuja extensão melhor corresponda com a extensão do texto selecionado no editor.</span><span class="sxs-lookup"><span data-stu-id="2e028-147">The visualizer highlights the item in the tree whose span best matches the span of the text selected in the editor.</span></span>

<span data-ttu-id="2e028-148">O visualizador atualiza a árvore para corresponder às modificações no arquivo de código ativo.</span><span class="sxs-lookup"><span data-stu-id="2e028-148">The visualizer refreshes the tree to match modifications in the active code file.</span></span> <span data-ttu-id="2e028-149">Adicione uma chamada a `Console.WriteLine()` dentro de `Main()`.</span><span class="sxs-lookup"><span data-stu-id="2e028-149">Add a call to `Console.WriteLine()` inside `Main()`.</span></span> <span data-ttu-id="2e028-150">Conforme você digita, o visualizador atualiza a árvore.</span><span class="sxs-lookup"><span data-stu-id="2e028-150">As you type, the visualizer refreshes the tree.</span></span>

<span data-ttu-id="2e028-151">Pare de digitar quando já tiver digitado `Console.`.</span><span class="sxs-lookup"><span data-stu-id="2e028-151">Pause typing once you have typed `Console.`.</span></span> <span data-ttu-id="2e028-152">A árvore tem alguns itens coloridos em rosa.</span><span class="sxs-lookup"><span data-stu-id="2e028-152">The tree has some items colored in pink.</span></span> <span data-ttu-id="2e028-153">Neste ponto, há erros (também conhecidos como "Diagnóstico") no código digitado.</span><span class="sxs-lookup"><span data-stu-id="2e028-153">At this point, there are errors (also referred to as ‘Diagnostics’) in the typed code.</span></span> <span data-ttu-id="2e028-154">Esses erros são anexados a nós, tokens e trívia na árvore de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="2e028-154">These errors are attached to nodes, tokens, and trivia in the syntax tree.</span></span> <span data-ttu-id="2e028-155">O visualizador mostra quais itens têm erros anexados a eles, realçando a tela de fundo em rosa.</span><span class="sxs-lookup"><span data-stu-id="2e028-155">The visualizer shows you which items have errors attached to them highlighting the background in pink.</span></span> <span data-ttu-id="2e028-156">Você pode inspecionar os erros em qualquer item colorido em rosa passando o mouse sobre o item.</span><span class="sxs-lookup"><span data-stu-id="2e028-156">You can inspect the errors on any item colored pink by hovering over the item.</span></span> <span data-ttu-id="2e028-157">O visualizador exibe somente erros sintáticos (os erros relacionados à sintaxe do código digitado); erros semânticos não são exibidos.</span><span class="sxs-lookup"><span data-stu-id="2e028-157">The visualizer only displays syntactic errors (those errors related to the syntax of the typed code); it doesn't display any semantic errors.</span></span>
 
## <a name="syntax-graphs"></a><span data-ttu-id="2e028-158">Gráficos de sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e028-158">Syntax Graphs</span></span>

<span data-ttu-id="2e028-159">Clique com o botão direito do mouse em qualquer item da árvore e clique em **Exibir gráfico de sintaxe direcionado**.</span><span class="sxs-lookup"><span data-stu-id="2e028-159">Right click on any item in the tree and click on **View Directed Syntax Graph**.</span></span> 

<span data-ttu-id="2e028-160">O visualizador exibe uma representação gráfica da subárvore com raiz no item selecionado.</span><span class="sxs-lookup"><span data-stu-id="2e028-160">The visualizer displays a graphical representation of the subtree rooted at the selected item.</span></span> <span data-ttu-id="2e028-161">Repita essas etapas para o nó **MethodDeclaration** correspondente ao método `Main()` no exemplo de C#.</span><span class="sxs-lookup"><span data-stu-id="2e028-161">Try these steps for the **MethodDeclaration** node corresponding to the `Main()` method in the C# example.</span></span> <span data-ttu-id="2e028-162">O visualizador exibe um gráfico de sintaxe que tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="2e028-162">The visualizer displays a syntax graph that looks as follows:</span></span>

![Exibindo um gráfico de sintaxe de C#](media/csharp-syntax-graph.png)

<span data-ttu-id="2e028-164">Repita o mesmo para o nó **SubBlock** correspondente ao método `Main()` no exemplo anterior do VB.</span><span class="sxs-lookup"><span data-stu-id="2e028-164">Try the same for the **SubBlock** node corresponding to the `Main()` method in the preceding VB example.</span></span> <span data-ttu-id="2e028-165">O visualizador exibe um gráfico de sintaxe que tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="2e028-165">The visualizer displays a syntax graph that looks as follows:</span></span>

![Exibindo um gráfico de sintaxe do VB](media/visual-basic-syntax-graph.png)

<span data-ttu-id="2e028-167">O visualizador de gráfico de sintaxe tem uma opção para exibir uma legenda de seu esquema de cores.</span><span class="sxs-lookup"><span data-stu-id="2e028-167">The syntax graph viewer has an option to display a legend its coloring scheme.</span></span> <span data-ttu-id="2e028-168">Você também pode passar o mouse sobre itens específicos no gráfico de sintaxe para exibir as respectivas propriedades.</span><span class="sxs-lookup"><span data-stu-id="2e028-168">You can also hover over individual items in the syntax graph with the mouse to view the properties corresponding to that item.</span></span>

<span data-ttu-id="2e028-169">Você pode exibir gráficos de sintaxe de itens diferentes da árvore repetidamente e os gráficos serão sempre exibidos na mesma janela no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2e028-169">You can view syntax graphs for different items in the tree repeatedly and the graphs will always be displayed in the same window inside Visual Studio.</span></span> <span data-ttu-id="2e028-170">Você pode encaixar essa janela em um local conveniente no Visual Studio para não precisar alternar entre as guias para exibir um novo gráfico de sintaxe.</span><span class="sxs-lookup"><span data-stu-id="2e028-170">You can dock this window at a convenient location inside Visual Studio so that you don’t have to switch between tabs to view a new syntax graph.</span></span> <span data-ttu-id="2e028-171">A parte inferior, abaixo das janelas do editor de código, geralmente é conveniente.</span><span class="sxs-lookup"><span data-stu-id="2e028-171">The bottom, below code editor windows, is often convenient.</span></span>

<span data-ttu-id="2e028-172">Veja o layout de encaixe para usar com a janela de ferramentas do visualizador e a janela do gráfico de sintaxe:</span><span class="sxs-lookup"><span data-stu-id="2e028-172">Here is the docking layout to use with the visualizer tool window and the syntax graph window:</span></span>

![Um layout de encaixe para a janela de gráfico de sintaxe e o visualizador](media/docking-layout.png)

<span data-ttu-id="2e028-174">Outra opção é colocar a janela de gráfico de sintaxe em um segundo monitor, em uma configuração de dois monitores.</span><span class="sxs-lookup"><span data-stu-id="2e028-174">Another option is to put the syntax graph window on a second monitor, in a dual monitor setup.</span></span>

# <a name="inspecting-semantics"></a><span data-ttu-id="2e028-175">Inspecionando semântica</span><span class="sxs-lookup"><span data-stu-id="2e028-175">Inspecting semantics</span></span>

<span data-ttu-id="2e028-176">O Visualizador de sintaxe possibilita uma inspeção rudimentar de símbolos e informações semânticas.</span><span class="sxs-lookup"><span data-stu-id="2e028-176">The Syntax Visualizer enables rudimentary inspection of symbols and semantic information.</span></span> <span data-ttu-id="2e028-177">Digite `double x = 1 + 1;` dentro de Main() no exemplo de C#.</span><span class="sxs-lookup"><span data-stu-id="2e028-177">Type `double x = 1 + 1;` inside Main() in the C# example.</span></span> <span data-ttu-id="2e028-178">Em seguida, selecione a expressão `1 + 1` na janela do editor de código.</span><span class="sxs-lookup"><span data-stu-id="2e028-178">Then, select the expression `1 + 1` in the code editor window.</span></span> <span data-ttu-id="2e028-179">O visualizador realça o nó **AddExpression** no visualizador.</span><span class="sxs-lookup"><span data-stu-id="2e028-179">The visualizer highlights the **AddExpression** node in the visualizer.</span></span> <span data-ttu-id="2e028-180">Clique com o botão direito do mouse nesse **AddExpression** e clique em **Exibir Symbol (se houver)**.</span><span class="sxs-lookup"><span data-stu-id="2e028-180">Right click on this **AddExpression** and click on **View Symbol (if any)**.</span></span> <span data-ttu-id="2e028-181">Observe que a maioria dos itens de menu tem o qualificador "se houver".</span><span class="sxs-lookup"><span data-stu-id="2e028-181">Notice that most of the menu items have the "if any" qualifier.</span></span> <span data-ttu-id="2e028-182">O Visualizador de sintaxe inspeciona as propriedades de um Nó, incluindo propriedades que podem não estar presentes em todos os nós.</span><span class="sxs-lookup"><span data-stu-id="2e028-182">The Syntax Visualizer inspects properties of a Node, including properties that may not be present for all nodes.</span></span> 

<span data-ttu-id="2e028-183">A grade de propriedade do visualizador é atualizada conforme mostrado na figura a seguir: o símbolo da expressão é um **SynthesizedIntrinsicOperatorSymbol** com **Kind = Method**.</span><span class="sxs-lookup"><span data-stu-id="2e028-183">The property grid in the visualizer updates as shown in the following figure: The symbol for the expression is a **SynthesizedIntrinsicOperatorSymbol** with **Kind = Method**.</span></span>

![Propriedades Symbol](media/symbol-properties.png)

<span data-ttu-id="2e028-185">Experimente **Exibir TypeSymbol (se houver)** para o mesmo nó **AddExpression**.</span><span class="sxs-lookup"><span data-stu-id="2e028-185">Try **View TypeSymbol (if any)** for the same **AddExpression** node.</span></span> <span data-ttu-id="2e028-186">A grade de propriedade no visualizador é atualizada, conforme mostrado na figura a seguir, indicando que o tipo da expressão selecionada é `Int32`.</span><span class="sxs-lookup"><span data-stu-id="2e028-186">The property grid in the visualizer updates as shown in the following figure, indicating that the type of the selected expression is `Int32`.</span></span>

![Propriedades TypeSymbol](media/type-symbol-properties.png)

<span data-ttu-id="2e028-188">Experimente **Exibir TypeSymbol Convertido (se houver)** para o mesmo nó **AddExpression**.</span><span class="sxs-lookup"><span data-stu-id="2e028-188">Try **View Converted TypeSymbol (if any)** for the same **AddExpression** node.</span></span> <span data-ttu-id="2e028-189">A grade de propriedade é atualizada, indicando que, embora o tipo da expressão seja `Int32`, o tipo convertido da expressão é `Double`, conforme mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e028-189">The property grid updates indicating that although the type of the expression is `Int32`, the converted type of the expression is `Double` as shown in the following figure.</span></span> <span data-ttu-id="2e028-190">Esse nó inclui informações de símbolo de tipo convertido porque a expressão `Int32` ocorre em um contexto em que deve ser convertida em um `Double`.</span><span class="sxs-lookup"><span data-stu-id="2e028-190">This node includes converted type symbol information because the `Int32` expression occurs in a context where it must be converted to a `Double`.</span></span> <span data-ttu-id="2e028-191">Essa conversão satisfaz o tipo `Double` especificado para a variável `x` no lado esquerdo do operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="2e028-191">This conversion satisfies the `Double` type specified for the variable `x` on the left-hand side of the assignment operator.</span></span>

![Propriedades TypeSymbol convertidas](media/converted-type-symbol-properties.png)

<span data-ttu-id="2e028-193">Por fim, experimente **Exibir Valor Constante (se houver)** para o mesmo nó **AddExpression**.</span><span class="sxs-lookup"><span data-stu-id="2e028-193">Finally, try **View Constant Value (if any)** for the same **AddExpression** node.</span></span> <span data-ttu-id="2e028-194">A grade de propriedade mostra que o valor da expressão é uma constante de tempo de compilação com o valor `2`.</span><span class="sxs-lookup"><span data-stu-id="2e028-194">The property grid shows that the value of the expression is a compile time constant with value `2`.</span></span>

![Um valor constante](media/constant-value.png)

<span data-ttu-id="2e028-196">O exemplo anterior também pode ser replicado no VB.</span><span class="sxs-lookup"><span data-stu-id="2e028-196">The preceding example can also be replicated in VB.</span></span> <span data-ttu-id="2e028-197">Digite `Dim x As Double = 1 + 1` em um arquivo do VB.</span><span class="sxs-lookup"><span data-stu-id="2e028-197">Type `Dim x As Double = 1 + 1` in a VB file.</span></span> <span data-ttu-id="2e028-198">Selecione a expressão `1 + 1` na janela do editor de código.</span><span class="sxs-lookup"><span data-stu-id="2e028-198">Select the expression `1 + 1` in the code editor window.</span></span> <span data-ttu-id="2e028-199">O visualizador realça o nó **AddExpression** correspondente no visualizador.</span><span class="sxs-lookup"><span data-stu-id="2e028-199">The visualizer highlights the corresponding **AddExpression** node in the visualizer.</span></span> <span data-ttu-id="2e028-200">Repita as etapas anteriores para esta **AddExpression** e você verá resultados idênticos.</span><span class="sxs-lookup"><span data-stu-id="2e028-200">Repeat the preceding steps for this **AddExpression** and you should see identical results.</span></span>

<span data-ttu-id="2e028-201">Examine mais código no VB.</span><span class="sxs-lookup"><span data-stu-id="2e028-201">Examine more code in VB.</span></span> <span data-ttu-id="2e028-202">Atualize seu arquivo principal do VB com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="2e028-202">Update your main VB file with the following code:</span></span>

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

<span data-ttu-id="2e028-203">Esse código introduz um alias chamado `C` que mapeia para o tipo `System.Console` na parte superior do arquivo e usa esse alias em `Main()`.</span><span class="sxs-lookup"><span data-stu-id="2e028-203">This code introduces an alias named `C` that maps to the type `System.Console` at the top of the file and uses this alias inside `Main()`.</span></span> <span data-ttu-id="2e028-204">Selecione o uso desse alias, o `C` em `C.WriteLine()`, dentro do método `Main()`.</span><span class="sxs-lookup"><span data-stu-id="2e028-204">Select the use of this alias, the `C` in `C.WriteLine()`, inside the `Main()` method.</span></span> <span data-ttu-id="2e028-205">O visualizador seleciona o nó **IdentifierName** correspondente no visualizador.</span><span class="sxs-lookup"><span data-stu-id="2e028-205">The visualizer selects the corresponding **IdentifierName** node in the visualizer.</span></span> <span data-ttu-id="2e028-206">Clique com botão direito do mouse nesse nó e clique em **Exibir Symbol (se houver)**.</span><span class="sxs-lookup"><span data-stu-id="2e028-206">Right-click this node and click on **View Symbol (if any)**.</span></span> <span data-ttu-id="2e028-207">A grade de propriedade mostra que esse identificador é associado com o tipo `System.Console`, conforme mostrado na figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="2e028-207">The property grid indicates that this identifier is bound to the type `System.Console` as shown in the following figure:</span></span>

![Propriedades Symbol](media/symbol-visual-basic.png)

<span data-ttu-id="2e028-209">Experimente **Exibir AliasSymbol (se houver)** para o mesmo nó **IdentifierName**.</span><span class="sxs-lookup"><span data-stu-id="2e028-209">Try **View AliasSymbol (if any)** for the same **IdentifierName** node.</span></span> <span data-ttu-id="2e028-210">A grade de propriedade mostra que o identificador é um alias com nome `C`, que é associado com o destino `System.Console`.</span><span class="sxs-lookup"><span data-stu-id="2e028-210">The property grid indicates the identifier is an alias with name `C` that is bound to the `System.Console` target.</span></span> <span data-ttu-id="2e028-211">Em outras palavras, a grade de propriedade fornece informações sobre o **AliasSymbol** correspondente ao identificador `C`.</span><span class="sxs-lookup"><span data-stu-id="2e028-211">In other words, the property grid provides information regarding the **AliasSymbol** corresponding to the identifier `C`.</span></span>

![Propriedades AliasSymbol](media/alias-symbol.png)

<span data-ttu-id="2e028-213">Inspecione o símbolo correspondente a qualquer tipo, método e propriedade declarados.</span><span class="sxs-lookup"><span data-stu-id="2e028-213">Inspect the symbol corresponding to any declared type, method, property.</span></span> <span data-ttu-id="2e028-214">Selecione o nó correspondente no visualizador e clique em **Exibir Symbol (se houver)**.</span><span class="sxs-lookup"><span data-stu-id="2e028-214">Select the corresponding node in the visualizer and click on **View Symbol (if any)**.</span></span> <span data-ttu-id="2e028-215">Selecione o método `Sub Main()`, incluindo o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="2e028-215">Select the method `Sub Main()`, including the body of the method.</span></span> <span data-ttu-id="2e028-216">Clique em **Exibir Symbol (se houver)** para o nó **SubBlock** correspondente no visualizador.</span><span class="sxs-lookup"><span data-stu-id="2e028-216">Click on **View Symbol (if any)** for the corresponding **SubBlock** node in the visualizer.</span></span> <span data-ttu-id="2e028-217">A grade de propriedade mostra que o **MethodSymbol** deste **SubBlock** tem nome `Main` com o tipo de retorno `Void`.</span><span class="sxs-lookup"><span data-stu-id="2e028-217">The property grid shows the **MethodSymbol** for this **SubBlock** has name `Main` with return type `Void`.</span></span>

![Exibindo o símbolo de uma declaração de método](media/method-symbol.png)

<span data-ttu-id="2e028-219">Os exemplos de VB acima podem ser facilmente replicados em C#.</span><span class="sxs-lookup"><span data-stu-id="2e028-219">The above VB examples can be easily replicated in C#.</span></span> <span data-ttu-id="2e028-220">Digite `using C = System.Console;` no lugar de `Imports C = System.Console` para o alias.</span><span class="sxs-lookup"><span data-stu-id="2e028-220">Type `using C = System.Console;` in place of `Imports C = System.Console` for the alias.</span></span> <span data-ttu-id="2e028-221">As etapas anteriores em C# geram resultados idênticos na janela do visualizador.</span><span class="sxs-lookup"><span data-stu-id="2e028-221">The preceding steps in C# yield identical results in the visualizer window.</span></span>

<span data-ttu-id="2e028-222">As operações de inspeção semântica estão disponíveis somente em nós.</span><span class="sxs-lookup"><span data-stu-id="2e028-222">Semantic inspection operations are only available on nodes.</span></span> <span data-ttu-id="2e028-223">Elas não estão disponíveis em tokens nem trívia.</span><span class="sxs-lookup"><span data-stu-id="2e028-223">They are not available on tokens or trivia.</span></span> <span data-ttu-id="2e028-224">Nem todos os nós têm informações semânticas interessantes para inspecionar.</span><span class="sxs-lookup"><span data-stu-id="2e028-224">Not all nodes have interesting semantic information to inspect.</span></span> <span data-ttu-id="2e028-225">Quando um nó não tem informações semânticas interessantes, clicar em **Exibir \* Symbol (se houver)** mostrará uma grade de propriedade em branco.</span><span class="sxs-lookup"><span data-stu-id="2e028-225">When a node doesn't have interesting semantic information, clicking on **View \* Symbol (if any)** shows a blank property grid.</span></span>

<span data-ttu-id="2e028-226">Você pode ler mais sobre as APIs para executar análise semântica no documento de visão geral [Trabalhar com semântica](work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="2e028-226">You can read more about APIs for performing semantic analysis in the [Work with semantics](work-with-semantics.md) overview document.</span></span>

## <a name="closing-the-syntax-visualizer"></a><span data-ttu-id="2e028-227">Fechando o visualizador de sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e028-227">Closing the syntax visualizer</span></span>

<span data-ttu-id="2e028-228">Você pode fechar a janela do visualizador quando não a estiver usando para examinar o código-fonte.</span><span class="sxs-lookup"><span data-stu-id="2e028-228">You can close the visualizer window when you are not using it to examine source code.</span></span> <span data-ttu-id="2e028-229">O visualizador de sintaxe atualiza a exibição enquanto você navega pelo código, editando e alterando-o.</span><span class="sxs-lookup"><span data-stu-id="2e028-229">The syntax visualizer updates its display as you navigate through code, editing and changing source.</span></span> <span data-ttu-id="2e028-230">Ele poderá se tornar uma distração quando você não estiver usando.</span><span class="sxs-lookup"><span data-stu-id="2e028-230">It can get distracting when you are not using it.</span></span> 