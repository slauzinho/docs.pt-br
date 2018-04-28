### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a><span data-ttu-id="9fd3a-101">Elementos DataTemplate do WPF agora são visíveis à UIA</span><span class="sxs-lookup"><span data-stu-id="9fd3a-101">WPF DataTemplate elements are now visible to UIA</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9fd3a-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9fd3a-102">Details</span></span>|<span data-ttu-id="9fd3a-103">Anteriormente, os elementos <xref:System.Windows.DataTemplate?displayProperty=name> eram invisíveis à Automação da Interface do Usuário.</span><span class="sxs-lookup"><span data-stu-id="9fd3a-103">Previously, <xref:System.Windows.DataTemplate?displayProperty=name> elements were invisible to UI Automation.</span></span> <span data-ttu-id="9fd3a-104">A partir da versão 4.5, a Automação da Interface do Usuário detectar esses elementos.</span><span class="sxs-lookup"><span data-stu-id="9fd3a-104">Beginning in 4.5, UI Automation will detect these elements.</span></span> <span data-ttu-id="9fd3a-105">Isso é útil em muitos casos, mas pode arruinar os testes que dependem das árvores UIA que não contêm elementos <xref:System.Windows.DataTemplate?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="9fd3a-105">This is useful in many cases, but can break tests that depend on UIA trees not containing <xref:System.Windows.DataTemplate?displayProperty=name> elements.</span></span>|
|<span data-ttu-id="9fd3a-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="9fd3a-106">Suggestion</span></span>|<span data-ttu-id="9fd3a-107">Os testes de Automação da Interface do Usuário para esse aplicativo talvez precisem ser atualizados para contabilizar a árvore UIA agora, incluindo elementos <xref:System.Windows.DataTemplate?displayProperty=name> anteriormente invisíveis.</span><span class="sxs-lookup"><span data-stu-id="9fd3a-107">UI Automation tests for this app may need updated to account for the UIA tree now including previously invisible <xref:System.Windows.DataTemplate?displayProperty=name> elements.</span></span> <span data-ttu-id="9fd3a-108">Por exemplo, os testes que esperam que alguns elementos fiquem próximos uns dos outros agora podem precisar esperar elementos UIA anteriormente invisíveis entre eles.</span><span class="sxs-lookup"><span data-stu-id="9fd3a-108">For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between.</span></span> <span data-ttu-id="9fd3a-109">Ou os testes que dependem de determinadas contagens ou de índices para elementos UIA talvez precisem ser atualizados com novos valores.</span><span class="sxs-lookup"><span data-stu-id="9fd3a-109">Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.</span></span>|
|<span data-ttu-id="9fd3a-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="9fd3a-110">Scope</span></span>|<span data-ttu-id="9fd3a-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="9fd3a-111">Edge</span></span>|
|<span data-ttu-id="9fd3a-112">Versão</span><span class="sxs-lookup"><span data-stu-id="9fd3a-112">Version</span></span>|<span data-ttu-id="9fd3a-113">4.5</span><span class="sxs-lookup"><span data-stu-id="9fd3a-113">4.5</span></span>|
|<span data-ttu-id="9fd3a-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="9fd3a-114">Type</span></span>|<span data-ttu-id="9fd3a-115">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9fd3a-115">Runtime</span></span>|
|<span data-ttu-id="9fd3a-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="9fd3a-116">Affected APIs</span></span>|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|
