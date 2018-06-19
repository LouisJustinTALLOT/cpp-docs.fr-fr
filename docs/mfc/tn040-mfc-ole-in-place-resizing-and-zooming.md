---
title: ': OLE de MFC dans-Tn040 redimensionnement et zoom | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf8b90aed96135967167c8048f775fc7530f85d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385003"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040 : redimensionnement et zoom sur place MFC/OLE
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note traite des problèmes concernant la modification en place et détermine comment un serveur doit accomplir un zoom correct et un redimensionnement en place. Avec l'activation en place, le concept WYSIWYG est traité à un niveau supérieur dans la mesure où les conteneurs et les serveurs coopèrent entre eux, et interprètent en particulier la spécification OLE à peu près de la même manière.  
  
 En raison de l'interaction proche entre un conteneur et un serveur prenant en charge l'activation en place, il existe un certain nombre d'attentes de l'utilisateur qui doivent être maintenues :  
  
-   L'affichage de présentation (un métafichier créé dans la substitution de `COleServerItem::OnDraw`) doit apparaître exactement de la même manière que s'il était modifié (sauf que les outils d'édition ne sont pas visibles).  
  
-   Lorsque le conteneur zoome, la fenêtre de serveur doit zoomer également !  
  
-   Le conteneur et le serveur doivent afficher des objets de modification utilisant les mêmes mesures. Cela revient à utiliser un mode de mappage basé sur le nombre de *logique* pixels par pouce, non pas physiques pixels par pouce, lors du rendu sur le périphérique d’affichage.  
  
> [!NOTE]
>  Étant donné que l'activation en place s'applique uniquement aux éléments qui sont incorporés (non liés), le zoom s'applique uniquement aux objets incorporés. Vous pouvez voir des API dans `COleServerDoc` et `COleServerItem` permettant de zoomer. La raison de cette dichotomie est que seules les fonctions qui ne sont pas valides pour les éléments liés et incorporés sont dans `COleServerItem` (cela vous permet d'avoir une implémentation commune) et les fonctions qui sont valides uniquement pour les objets incorporés figurent dans la classe `COleServerDoc` (du point de vue du serveur, c'est `document` qui est incorporé).  
  
 La majorité de la charge est placée sur l'implémenteur du serveur, car le serveur doit avoir connaissance du facteur de zoom du conteneur et modifier son interface de modification comme il convient. Mais comment le serveur détermine-t-il le facteur de zoom à l’aide de conteneur  
  
## <a name="mfc-support-for-zooming"></a>Prise en charge du zoom par MFC  
 Le facteur de zoom actuel peut être déterminé en appelant `COleServerDoc::GetZoomFactor`. Appeler cette fonction lorsque le document n'est pas actif en place a toujours pour résultat un facteur de zoom de 100 % (ou un rapport de 1:1). L'appeler lorsqu'il est actif en place peut retourner un autre résultat que 100 %.  
  
 Pour obtenir un exemple de zoom correct, consultez l’exemple OLE MFC [HIERSVR](../visual-cpp-samples.md). Le zoom dans HIERSVR est compliqué du fait qu'il affiche le texte, et le texte, en général, n'évolue pas de façon linéaire (conseils, conventions typographiques, largeurs et hauteurs de conception compliquent la question). Néanmoins, HIERSVR est une référence sensée pour implémenter le zoom correctement et n’est donc le tutoriel MFC [SCRIBBLE](../visual-cpp-samples.md) (étape 7).  
  
 `COleServerDoc::GetZoomFactor` détermine le facteur de zoom d'après plusieurs mesures disponibles dans le conteneur ou dans l'implémentation de vos classes `COleServerItem` et `COleServerDoc`. En bref, le facteur de zoom courant est déterminé par la formule suivante :  
  
```  
Position Rectangle (PR) / Container Extent (CE)  
```  
  
 La valeur POSITION RECTANGLE est déterminée par le conteneur. Elle est retournée au serveur lors de l'activation en place lorsque `COleClientItem::OnGetItemPosition` est appelé et est mis à jour au moment où le conteneur appelle `COleServerDoc::OnSetItemRects` du serveur (avec un appel à `COleClientItem::SetItemRects`).  
  
 La valeur CONTAINER EXTENT est légèrement plus complexe à calculer. Si le conteneur a appelé `COleServerItem::OnSetExtent` (par un appel à `COleClientItem::SetExtent`), alors la valeur CONTAINER EXTENT est convertie en pixels basée sur le nombre de pixels par pouce logique. Si le conteneur n'a pas appelé SetExtent (ce qui est généralement le cas), alors la valeur CONTAINER EXTENT est la taille retournée par `COleServerItem::OnGetExtent`. Par conséquent, si le conteneur n’a pas appelé SetExtent, le framework suppose que si c’était le conteneur aurait appelé avec 100 % de l’extension naturelle (la valeur retournée par **COleServerItem::GetExtent**). Autrement dit, le framework suppose que le conteneur affiche 100 % (ni plus, ni moins) de l'élément.  
  
 Il est important de noter que même si `COleServerItem::OnSetExtent` et `COleServerItem::OnGetExtent` ont des noms semblables, ils ne manipulent pas le même attribut de l'élément. `OnSetExtent` est appelé pour indiquer au serveur quelle quantité de l'objet est visible dans le conteneur (quel que soit le facteur de zoom) et `OnGetExtent` est appelé par le conteneur afin de déterminer la taille idéale de l'objet.  
  
 En consultant chacune des interfaces API en jeu, vous pouvez obtenir une image plus claire :  
  
## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent  
 Cette fonction doit retourner la "taille naturelle" en unités HIMETRIC de l'élément. Le meilleur moyen de visualiser la "taille naturelle" consiste à la définir comme la taille à laquelle il peut apparaître une fois imprimé. La valeur retournée est ici constante pour le contenu d'un élément donné (comme un métafichier, qui est constant pour un élément particulier). Cette valeur ne change pas lorsque le zoom est appliqué à l'élément. Elle ne change généralement pas lorsque le conteneur donne à l'élément plus ou moins d'espace en appelant `OnSetExtent`. Un exemple de modification peut être celui d'un simple éditeur de texte sans fonction de "marge" qui a inclus le texte en fonction de la dernière extension envoyée par le conteneur. Si un serveur est modifié, le serveur doit probablement définir le bit OLEMISC_RECOMPOSEONRESIZE dans le registre système (consultez la documentation OLESDK pour plus d'informations sur cette option).  
  
## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent  
 Cette fonction est appelée lorsque le conteneur montre "plus ou moins" l'objet. La plupart des conteneurs n'effectuent pas du tout l'appel. L'implémentation par défaut fournit la dernière valeur acceptée du conteneur dans "m_sizeExtent", qui est utilisé dans `COleServerDoc::GetZoomFactor` lors du calcul de la valeur CONTAINER EXTENT décrite ci-dessus.  
  
## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects  
 Cette fonction est appelée uniquement lorsque le document est actif en place. Elle est appelée lorsque le conteneur met à jour soit la position, soit le détourage appliqué à l'élément. La valeur POSITION RECTANGLE, comme présentée ci-dessus, fournit le numérateur de calcul du facteur de zoom. Un serveur peut demander que la position de l'élément soit modifiée en appelant `COleServerDoc::RequestPositionChange`. Le conteneur peut ou peut ne pas répondre à cette demande en appelant `OnSetItemRects` (avec un appel à **COleServerItem::SetItemRects**).  
  
## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw  
 Il est important de savoir que le métafichier créé en entrant `COleServerItem::OnDraw` produit exactement le même métafichier, quel que soit le facteur de zoom actuel. Le conteneur mettra à l'échelle le métafichier comme il convient. Il s'agit d'une distinction importante entre `OnDraw` de la vue et `OnDraw`de l'élément du serveur. La vue gère le zoom, l’élément crée simplement un *zoomable* métafichier et laisse le conteneur faire le zoom approprié.  
  
 Le meilleur moyen d'assurer que le serveur fonctionne correctement consiste à utiliser l'implémentation `COleServerDoc::GetZoomFactor` si votre document est actif en place.  
  
## <a name="mfc-support-for-in-place-resizing"></a>Prise en charge MFC pour le redimensionnement en place  
 MFC implémente entièrement l'interface de redimensionnement en place comme décrit dans la spécification OLE 2. L’interface utilisateur est prise en charge par le `COleResizeBar` classe, un message personnalisé **WM_SIZECHILD**et de ce message dans un traitement spécial `COleIPFrameWnd`.  
  
 Vous pouvez vouloir implémenter une gestion différente de ce message que celle fournie par le framework. Comme décrit ci-dessus, le framework conserve les résultats de redimensionnement en place jusqu'à un conteneur — le serveur répond au changement du facteur de zoom. Si le conteneur réagit en définissant les deux valeurs CONTAINER EXTENT et POSITION RECTANGLE lors du traitement de `COleClientItem::OnChangeItemPosition` (appelé à la suite d'un appel à `COleServerDoc::RequestPositionChange`), alors le rendimensionnement en place donnera un élément apparaissant "pratiquement" dans la fenêtre de modification. Si le conteneur réagit en définissant uniquement la valeur POSITION RECTANGLE pendant le traitement de `COleClientItem::OnChangeItemPosition`, le facteur de zoom change et l'élément est lu comme étant "zoomé".  
  
 Un serveur peut contrôler (à un certain degré) ce qui se produit lors de la négociation. Une feuille de calcul, par exemple peut choisir d'afficher plus ou moins de cellules lorsque l'utilisateur redimensionne la fenêtre en modifiant l'élément en place. Un traitement de texte peut choisir de modifier les "marges de page" pour qu'elles soient identiques à la fenêtre et ré-inclure le texte dans les nouvelles marges. Les serveurs implémentent cela en modifiant l'extension naturelle (la valeur retournée par `COleServerItem::OnGetExtent`) lorsque le redimensionnement est effectué. Cela entraîne la modification des deux valeurs POSITION RECTANGLE et CONTAINER EXTENT par le même volume, ce qui donne le même facteur de zoom, mais une plus grande ou plus petite zone d'affichage. En outre, la plupart du document est visible dans un métafichier généré par `OnDraw`. Dans ce cas, le document lui-même change lorsque l'utilisateur redimensionne l'élément, et non seulement la zone d'affichage.  
  
 Vous pouvez implémenter un redimensionnement personnalisé tout en tirant parti l’interface utilisateur fournie par `COleResizeBar` en remplaçant le **WM_SIZECHILD** de message dans votre `COleIPFrameWnd` classe. Pour plus d’informations sur les spécificités de **WM_SIZECHILD**, consultez [Note technique 24](../mfc/tn024-mfc-defined-messages-and-resources.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

