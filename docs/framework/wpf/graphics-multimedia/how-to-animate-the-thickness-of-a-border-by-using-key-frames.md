---
title: Como animar a espessura de uma borda usando quadros-chave
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: a601fd6779a4d912166366652435aff9ae37613f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421404"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>Como animar a espessura de uma borda usando quadros-chave
Este exemplo mostra como animar a <xref:System.Windows.Controls.Control.BorderThickness%2A> propriedade de um <xref:System.Windows.Controls.Border>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> classe para animar a <xref:System.Windows.Controls.Control.BorderThickness%2A> propriedade de um <xref:System.Windows.Controls.Border>. Essa animação usa três quadros-chave da seguinte maneira:  
  
1.  Durante o primeiro meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> classe para aumentar gradualmente a espessura da borda. O exemplo usa <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> para criar um aumento linear suave entre valores.  
  
2.  No final do próximo meio segundo, usa uma instância da <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> classe para aumentar repentinamente a espessura da borda. Quadros chave discretos como aqueles derivam <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> criam saltos repentinos entre valores, ou seja, o movimento da animação é brusco.  
  
3.  Durante os dois segundos finais, usa uma instância da <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> classe para diminuir a espessura da borda. Quadros-chave spline, como aqueles derivam <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> criam uma transição variável entre valores de acordo com os valores da <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> propriedade. Neste quadro-chave, a animação começa lentamente e acelera exponencialmente na direção do final do segmento de tempo.  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Para ver o exemplo completo, consulte [Exemplo de animação de quadro-chave](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [Visão geral das animações de quadro-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Tópicos explicativos sobre quadros-chave](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [Animar um valor de BorderThickness](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
