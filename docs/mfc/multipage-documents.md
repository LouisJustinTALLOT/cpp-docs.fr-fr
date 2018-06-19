---
title: Documents multipages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- pagination [MFC]
- overriding [MFC], View class functions for printing
- OnPrepareDC method [MFC]
- CPrintInfo structure [MFC], multipage documents
- OnEndPrinting method [MFC]
- protocols [MFC], printing protocol
- document pages vs. printer pages [MFC]
- printer mode [MFC]
- printing [MFC], multipage documents
- printers [MFC], printer mode
- documents [MFC], printing
- OnPreparePrinting method [MFC]
- OnPrint method [MFC]
- DoPreparePrinting method and pagination [MFC]
- OnDraw method [MFC], printing
- pagination [MFC], printing multipage documents
- printing [MFC], protocol
- pages [MFC], printing
- OnBeginPrinting method [MFC]
- multipage documents [MFC]
- printing [MFC], pagination
- documents [MFC], paginating
ms.assetid: 69626b86-73ac-4b74-b126-9955034835ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24ad3e99399e4d5db45606accfd58512f3950f26
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355270"
---
# <a name="multipage-documents"></a>Documents multipages
Cet article décrit le protocole d'impression Windows et explique comment imprimer des documents qui contiennent plusieurs pages. L'article couvre les rubriques suivantes :  
  
-   [Protocole d’impression](#_core_the_printing_protocol)  
  
-   [Remplacement des fonctions de classe d’affichage](#_core_overriding_view_class_functions)  
  
-   [Pagination](#_core_pagination)  
  
-   [Pages de l’imprimante et les pages du document](#_core_printer_pages_vs.._document_pages)  
  
-   [Pagination de délai d’impression](#_core_print.2d.time_pagination)  
  
##  <a name="_core_the_printing_protocol"></a> Le protocole d’impression  
 Pour imprimer un document multipage, le framework et l'affichage interagissent de la façon suivante. L’infrastructure affiche d’abord le **impression** boîte de dialogue, crée un contexte de périphérique pour l’imprimante, puis appelle la [StartDoc](../mfc/reference/cdc-class.md#startdoc) fonction membre de la [CDC](../mfc/reference/cdc-class.md) objet. Ensuite, pour chaque page du document, le framework appelle la [StartPage](../mfc/reference/cdc-class.md#startpage) fonction membre de la `CDC` d’objet, fait en sorte que l’objet de vue pour imprimer la page, puis appelle le [EndPage](../mfc/reference/cdc-class.md#endpage) fonction membre. Si le mode d’impression doit être modifié avant de démarrer une page spécifique, la vue appelle [ResetDC](../mfc/reference/cdc-class.md#resetdc), les mises à jour le [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) structure contenant les informations du mode nouvelle imprimante. Lorsque la totalité du document a été imprimé, le framework appelle la [EndDoc](../mfc/reference/cdc-class.md#enddoc) fonction membre.  
  
##  <a name="_core_overriding_view_class_functions"></a> Remplacement des fonctions de classe d’affichage  
 Le [CView](../mfc/reference/cview-class.md) classe définit plusieurs fonctions membres qui sont appelées par l’infrastructure lors de l’impression. Lorsque vous remplacez ces fonctions dans votre classe d'affichage, vous fournissez les connexions entre la logique d'impression du framework et la logique d'impression de votre classe d'affichage. Le tableau suivant répertorie ces fonctions membres.  
  
### <a name="cviews-overridable-functions-for-printing"></a>Les fonctions substituables de CView pour l'impression  
  
|Name|Motif de remplacement|  
|----------|---------------------------|  
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|Pour insérer des valeurs dans la boîte de dialogue Imprimer, notamment la longueur du document|  
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|Pour allouer les polices ou d'autres ressources GDI|  
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|Pour paramétrer les attributs du contexte de périphérique pour une page spécifique, ou calculer la pagination de délai d'impression|  
|[OnPrint](../mfc/reference/cview-class.md#onprint)|Pour imprimer une page de données|  
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|Pour libérer des ressources GDI|  
  
 Vous pouvez effectuer un traitement d'impression dans d'autres fonctions également, mais ces fonctions sont celles qui pilotent le processus d'impression.  
  
 L'illustration suivante montre les étapes impliquées dans le processus d'impression et indique où chaque `CView` des fonctions membres de l'impression est appelé. Le reste de cet article explique la plupart de ces étapes plus en détail. Des parties supplémentaires du processus d’impression sont décrites dans l’article [allocation des ressources GDI](../mfc/allocating-gdi-resources.md).  
  
 ![L’impression de processus en boucle](../mfc/media/vc37c71.gif "vc37c71")  
La boucle d'impression  
  
##  <a name="_core_pagination"></a> Pagination  
 Le framework stocke une grande partie des informations relatives à un travail d’impression dans un [CPrintInfo](../mfc/reference/cprintinfo-structure.md) structure. Plusieurs valeurs dans `CPrintInfo` se rapportent à la pagination ; ces valeurs sont accessibles comme indiqué dans le tableau suivant.  
  
### <a name="page-number-information-stored-in-cprintinfo"></a>Les informations de numéro de page stockées dans CPrintInfo  
  
|Variable membre ou<br /><br /> nom(s) de la fonction|Numéro de page référencée|  
|-----------------------------------------------|----------------------------|  
|`GetMinPage`/`SetMinPage`|Première page du document|  
|`GetMaxPage`/`SetMaxPage`|Dernière page du document|  
|`GetFromPage`|Première page à imprimer|  
|`GetToPage`|Dernière page à imprimer|  
|`m_nCurPage`|Page actuellement imprimée|  
  
 Les numéros de page commence à 1, c'est-à-dire, la première page est numérotée à 1, et non à 0. Pour plus d’informations sur ces événements et autres membres de [CPrintInfo](../mfc/reference/cprintinfo-structure.md), consultez la *référence MFC*.  
  
 Au début du processus d’impression, le framework appelle la vue [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) fonction membre, en passant un pointeur vers un `CPrintInfo` structure. L’Assistant Application fournit une implémentation de `OnPreparePrinting` qui appelle [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), une autre fonction membre de `CView`. `DoPreparePrinting` est la fonction qui affiche la boîte de dialogue Imprimer et crée un contexte de périphérique d'imprimante.  
  
 À ce stade, l'application ne connaît pas le nombre de pages contenues dans le document. Elle utilise les valeurs par défaut 1 et 0xFFFF pour les numéros des première et dernière pages du document. Si vous connaissez le nombre de pages contient votre document, substituez `OnPreparePrinting` et appelez [SetMaxPage]--brokenlink--(reference/cprintinfo-class.md#setmaxpage) pour la `CPrintInfo` avant de l’envoyer à la structure `DoPreparePrinting`. Cela vous permet de spécifier la longueur du document.  
  
 `DoPreparePrinting` affiche alors la boîte de dialogue Imprimer. Lorsque la valeur est renvoyée, la structure `CPrintInfo` contient les valeurs spécifiées par l'utilisateur. Si l'utilisateur ne souhaite imprimer qu'une seule plage de pages sélectionnées, il ou elle peut spécifier des numéros de page de début et de fin dans la boîte de dialogue Imprimer. Le framework récupère ces valeurs à l’aide de la `GetFromPage` et `GetToPage` fonctions de [CPrintInfo](../mfc/reference/cprintinfo-structure.md). Si l'utilisateur ne spécifie pas d'étendue de pages, le framework appelle `GetMinPage` et `GetMaxPage` et utilise les valeurs retournées pour imprimer le document.  
  
 Pour chaque page d’un document à imprimer, le framework appelle deux fonctions membres dans votre classe d’affichage, [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) et [OnPrint](../mfc/reference/cview-class.md#onprint)et le passe à chaque fonction deux paramètres : un pointeur vers un [ Capture de données modifiées](../mfc/reference/cdc-class.md) objet et un pointeur vers un `CPrintInfo` structure. Chaque fois que le framework appelle `OnPrepareDC` et `OnPrint`, il transmet une valeur différente dans le membre `m_nCurPage` de la structure `CPrintInfo`. De cette manière, le framework indique à l'affichage quelle page doit être imprimée.  
  
 Le [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) fonction membre est également utilisée pour afficher l’écran. Elle ajuste le contexte de périphérique avant que l'ajout n'ait lieu. `OnPrepareDC` sert un rôle semblable à l'impression, mais il existe des différences : d'abord, l'objet `CDC` représente le contexte de l'imprimante au lieu d'un contexte de périphérique, et ensuite, un objet `CPrintInfo` est transmis en tant que second paramètre. (Ce paramètre est **NULL** lorsque `OnPrepareDC` est appelé pour afficher l’écran.) Remplacez `OnPrepareDC` pour effectuer des ajustements dans le contexte de périphérique sur lequel la page est imprimée. Par exemple, vous pouvez déplacer l'origine de la fenêtre d'affichage et la zone de découpage pour garantir que la partie pertinente du document est imprimée.  
  
 Le [OnPrint](../mfc/reference/cview-class.md#onprint) fonction membre effectue l’impression réelle de la page. L’article [par défaut d’impression procédure](../mfc/how-default-printing-is-done.md) montre comment le framework appelle [OnDraw](../mfc/reference/cview-class.md#ondraw) avec un contexte de périphérique pour effectuer une impression. Plus précisément, le framework appelle `OnPrint` avec une structure `CPrintInfo` et un contexte de périphérique, et `OnPrint` passe le contexte de périphérique à `OnDraw`. Remplacez `OnPrint` pour exécuter un rendu qui doit être effectué uniquement lors de l'impression et pas pour l'affichage à l'écran. Par exemple, pour imprimer les en-têtes ou pieds de page (voir l’article [en-têtes et pieds de page](../mfc/headers-and-footers.md) pour plus d’informations). Ensuite, appelez `OnDraw` de la substitution de `OnPrint` pour effectuer les opérations communes au rendu à l'écran et à l'impression.  
  
 Le fait que `OnDraw` génère l'affichage à la fois à l'écran et à l'impression, signifie que votre application est WYSIWYG : "What you see is what you get (vous obtenez ce que vous voyez)". Toutefois, supposons que vous ne développiez pas une application WYSIWYG. Par exemple, prenez le cas d'un éditeur de texte qui utilise une police en gras pour l'impression mais affiche des codes de contrôle pour indiquer le texte en gras sur l'écran. Dans ce type de situation, vous utilisez `OnDraw` strictement pour l'écran. Lorsque vous remplacez `OnPrint`, remplacez l'appel à `OnDraw` par un appel à une fonction de dessin distincte. La fonction dessine le document de la manière dont il apparaît sur le papier, à l'aide des attributs que vous n'affichez pas sur l'écran.  
  
##  <a name="_core_printer_pages_vs.._document_pages"></a> Vs de Pages d’imprimante. Pages de document  
 Lorsque vous faites référence à des numéros de page, il est parfois nécessaire de distinguer le concept de page dans le cadre de l'imprimante et le concept de page dans le cadre d'un document. Du point de vue de l'imprimante, une page est une feuille de papier. Toutefois, une feuille de papier n'est pas nécessairement une page du document. Par exemple, si vous imprimez un bulletin d'informations, où les feuilles doivent être pliées, une feuille de papier peut contenir les première et dernière pages du document, côte à côte. De même, si vous imprimez une feuille de calcul, le document ne comprend pas les pages du tout. En revanche, une feuille de papier peut contenir des lignes allant de 1 à 20 et des colonnes de 6 à 10.  
  
 La page de tous les nombres dans les [CPrintInfo](../mfc/reference/cprintinfo-structure.md) structure font référence aux pages d’impression. Le framework appelle `OnPrepareDC` et `OnPrint` une fois pour chaque feuille de papier qui transite par l'imprimante. Lorsque vous remplacez le [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) de fonction pour spécifier la longueur du document, vous devez utiliser les pages de l’imprimante. Si une correspondance un-à-un est possible (autrement dit, une page d'impression est égale à une page de document), alors le processus est simplifié. Si, en revanche, les pages de documents et d'impression ne correspondent pas directement, vous devez les convertir entre elles. Par exemple, envisagez d'imprimer une feuille de calcul. En remplaçant `OnPreparePrinting`, vous devez calculer le nombre de feuilles de papier nécessaires pour imprimer la feuille de calcul entière, puis utiliser cette valeur en appelant la fonction membre `SetMaxPage` de `CPrintInfo`. De même, en remplaçant `OnPrepareDC`, vous devez convertir `m_nCurPage` en une plage de lignes et de colonnes qui apparaissent sur cette feuille en particulier, puis ajuster l'origine de la fenêtre d'affichage en conséquence.  
  
##  <a name="_core_print.2d.time_pagination"></a> Pagination de délai d’impression  
 Dans certains cas, il est possible que votre classe d'affichage ne connaisse pas à l'avance la longueur du document avant qu'il soit réellement imprimé. Par exemple, supposons que votre application n'est pas WYSIWYG, donc la longueur d'un document à l'écran ne correspond pas à sa longueur une fois imprimée.  
  
 Ceci pose un problème lorsque vous substituez [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) pour votre classe d’affichage : vous ne pouvez pas passer une valeur pour le `SetMaxPage` fonction de la [CPrintInfo](../mfc/reference/cprintinfo-structure.md) structure, car vous ne connaissez pas la longueur d’un document. Si l'utilisateur ne spécifie pas un numéro de page pour arrêter d'utiliser la boîte de dialogue Imprimer, le framework ne saura pas quand arrêter la boucle d'impression. La seule façon de déterminer l'arrêt de la boucle d'impression est d'imprimer le document et de voir à quel moment il se termine. La classe d'affichage doit vérifier la fin du document lorsqu'il est imprimé, puis d'avertir le framework lorsque la fin est atteinte.  
  
 Le framework s’appuie sur la classe d’affichage [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) fonction pour indiquer qu’il doit s’arrêter. Après chaque appel à `OnPrepareDC`, le framework active un membre de la structure `CPrintInfo` appelée `m_bContinuePrinting`. Sa valeur par défaut est **TRUE.** Dès lors qu'elle reste inchangée, le framework poursuit la boucle d'impression. Si elle est définie sur **FALSE**, le framework s’arrête. Pour exécuter la pagination de délai d’impression, substituez `OnPrepareDC` pour vérifier si la fin du document a été atteinte et définir `m_bContinuePrinting` à **FALSE** lorsqu’il a.  
  
 L’implémentation par défaut de `OnPrepareDC` définit `m_bContinuePrinting` à **FALSE** si la page actuelle est supérieure à 1. Cela signifie que si la longueur du document n'est pas spécifiée, le framework suppose que le document ne comporte qu'une seule page. La conséquence de ce fait est que vous devez être prudent lorsque vous appelez la version de la classe de base de `OnPrepareDC`. Ne supposez pas que `m_bContinuePrinting` sera **TRUE** après l’appel de la version de la classe de base.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [En-têtes et pieds de page](../mfc/headers-and-footers.md)  
  
-   [Allocation de ressources GDI](../mfc/allocating-gdi-resources.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Impression](../mfc/printing.md)   
 [CView (classe)](../mfc/reference/cview-class.md)   
 [CDC, classe](../mfc/reference/cdc-class.md)