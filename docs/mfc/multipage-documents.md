---
title: Documents multipages
ms.date: 11/19/2018
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
ms.openlocfilehash: 87912c06a40740d25530235ee421c6c8bfa11aab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370737"
---
# <a name="multipage-documents"></a>Documents multipages

Cet article décrit le protocole d'impression Windows et explique comment imprimer des documents qui contiennent plusieurs pages. L'article couvre les rubriques suivantes :

- [Protocole d’impression](#_core_the_printing_protocol)

- [Fonctions de classe de vue primordiales](#_core_overriding_view_class_functions)

- [Pagination](#_core_pagination)

- [Comparaison entre les pages d'impression et les pages de document](#_core_printer_pages_vs.._document_pages)

- [Pagination imprime-temps](#_core_print.2d.time_pagination)

## <a name="the-printing-protocol"></a><a name="_core_the_printing_protocol"></a>Le Protocole d’impression

Pour imprimer un document multipage, le framework et l'affichage interagissent de la façon suivante. Tout d’abord, le cadre affiche la boîte de dialogue **d’impression,** crée un contexte d’appareil pour l’imprimante, et appelle la fonction membre [StartDoc](../mfc/reference/cdc-class.md#startdoc) de [l’objet CDC.](../mfc/reference/cdc-class.md) Ensuite, pour chaque page du document, le cadre appelle `CDC` la fonction membre [StartPage](../mfc/reference/cdc-class.md#startpage) de l’objet, ordonne à l’objet de vue d’imprimer la page et appelle la fonction membre [EndPage.](../mfc/reference/cdc-class.md#endpage) Si le mode d’imprimante doit être modifié avant de démarrer une page particulière, la vue appelle [ResetDC](../mfc/reference/cdc-class.md#resetdc), qui met à jour la structure [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) contenant les nouvelles informations du mode imprimante. Lorsque l’ensemble du document a été imprimé, le cadre appelle la fonction membre [endDoc.](../mfc/reference/cdc-class.md#enddoc)

## <a name="overriding-view-class-functions"></a><a name="_core_overriding_view_class_functions"></a>Fonctions de classe de vue primordiales

La classe [CView](../mfc/reference/cview-class.md) définit plusieurs fonctions de membre qui sont appelées par le cadre lors de l’impression. Lorsque vous remplacez ces fonctions dans votre classe d'affichage, vous fournissez les connexions entre la logique d'impression du framework et la logique d'impression de votre classe d'affichage. Le tableau suivant répertorie ces fonctions membres.

### <a name="cviews-overridable-functions-for-printing"></a>Les fonctions substituables de CView pour l'impression

|Nom|Motif de remplacement|
|----------|---------------------------|
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|Pour insérer des valeurs dans la boîte de dialogue Imprimer, notamment la longueur du document|
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|Pour allouer les polices ou d'autres ressources GDI|
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|Pour paramétrer les attributs du contexte de périphérique pour une page spécifique, ou calculer la pagination de délai d'impression|
|[OnPrint](../mfc/reference/cview-class.md#onprint)|Pour imprimer une page de données|
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|Pour libérer des ressources GDI|

Vous pouvez effectuer un traitement d'impression dans d'autres fonctions également, mais ces fonctions sont celles qui pilotent le processus d'impression.

L'illustration suivante montre les étapes impliquées dans le processus d'impression et indique où chaque `CView` des fonctions membres de l'impression est appelé. Le reste de cet article explique la plupart de ces étapes plus en détail. D’autres parties du processus d’impression sont décrites dans l’article [Allocating GDI Resources](../mfc/allocating-gdi-resources.md).

![Processus de boucle d'impression](../mfc/media/vc37c71.gif "Processus de boucle d'impression") <br/>
La boucle d'impression

## <a name="pagination"></a><a name="_core_pagination"></a>Pagination

Le cadre stocke une grande partie de l’information sur un travail d’impression dans une structure [CPrintInfo.](../mfc/reference/cprintinfo-structure.md) Plusieurs valeurs dans `CPrintInfo` se rapportent à la pagination ; ces valeurs sont accessibles comme indiqué dans le tableau suivant.

### <a name="page-number-information-stored-in-cprintinfo"></a>Les informations de numéro de page stockées dans CPrintInfo

|Variable membre ou<br /><br /> nom(s) de la fonction|Numéro de page référencée|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|Première page du document|
|`GetMaxPage`/`SetMaxPage`|Dernière page du document|
|`GetFromPage`|Première page à imprimer|
|`GetToPage`|Dernière page à imprimer|
|`m_nCurPage`|Page actuellement imprimée|

Les numéros de page commence à 1, c'est-à-dire, la première page est numérotée à 1, et non à 0. Pour plus d’informations sur ces membres et d’autres de [CPrintInfo](../mfc/reference/cprintinfo-structure.md), voir la *référence MFC*.

Au début du processus d’impression, le cadre appelle la fonction de membre [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) de la vue, en passant un pointeur à une `CPrintInfo` structure. L’Assistant d’application `OnPreparePrinting` fournit une mise en œuvre `CView`de ce qui appelle [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), une autre fonction de membre de . `DoPreparePrinting` est la fonction qui affiche la boîte de dialogue Imprimer et crée un contexte de périphérique d'imprimante.

À ce stade, l'application ne connaît pas le nombre de pages contenues dans le document. Elle utilise les valeurs par défaut 1 et 0xFFFF pour les numéros des première et dernière pages du document. Si vous savez combien de pages `OnPreparePrinting` votre document a, remplacez et appelez [SetMaxPage]--brokenlink---(reference/cprintinfo-class.md-setmaxpage) pour la structure avant de l’envoyer `CPrintInfo` à `DoPreparePrinting`. Cela vous permet de spécifier la longueur du document.

`DoPreparePrinting` affiche alors la boîte de dialogue Imprimer. Lorsque la valeur est renvoyée, la structure `CPrintInfo` contient les valeurs spécifiées par l'utilisateur. Si l'utilisateur ne souhaite imprimer qu'une seule plage de pages sélectionnées, il ou elle peut spécifier des numéros de page de début et de fin dans la boîte de dialogue Imprimer. Le cadre récupère ces `GetFromPage` valeurs `GetToPage` à l’aide de [CPrintInfo](../mfc/reference/cprintinfo-structure.md)et des fonctions . Si l'utilisateur ne spécifie pas d'étendue de pages, le framework appelle `GetMinPage` et `GetMaxPage` et utilise les valeurs retournées pour imprimer le document.

Pour chaque page d’un document à imprimer, le cadre appelle deux fonctions de membre dans votre classe de vue, [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) et `CPrintInfo` [OnPrint](../mfc/reference/cview-class.md#onprint), et transmet chaque fonction deux paramètres : un pointeur vers un objet [CDC](../mfc/reference/cdc-class.md) et un pointeur vers une structure. Chaque fois que `OnPrepareDC` `OnPrint`le cadre appelle et , il passe une `CPrintInfo` valeur différente dans le *m_nCurPage* membre de la structure. De cette manière, le framework indique à l'affichage quelle page doit être imprimée.

La fonction membre [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) est également utilisée pour l’affichage de l’écran. Elle ajuste le contexte de périphérique avant que l'ajout n'ait lieu. `OnPrepareDC` sert un rôle semblable à l'impression, mais il existe des différences : d'abord, l'objet `CDC` représente le contexte de l'imprimante au lieu d'un contexte de périphérique, et ensuite, un objet `CPrintInfo` est transmis en tant que second paramètre. (Ce paramètre `OnPrepareDC` est **NULL** lorsqu’il est appelé pour l’affichage de l’écran.) Remplacer `OnPrepareDC` pour apporter des ajustements au contexte de l’appareil en fonction de la page imprimée. Par exemple, vous pouvez déplacer l'origine de la fenêtre d'affichage et la zone de découpage pour garantir que la partie pertinente du document est imprimée.

La fonction membre [OnPrint](../mfc/reference/cview-class.md#onprint) effectue l’impression réelle de la page. [L’article How Default Printing Is Done](../mfc/how-default-printing-is-done.md) montre comment le cadre appelle [OnDraw](../mfc/reference/cview-class.md#ondraw) avec un contexte d’imprimante pour effectuer l’impression. Plus précisément, le framework appelle `OnPrint` avec une structure `CPrintInfo` et un contexte de périphérique, et `OnPrint` passe le contexte de périphérique à `OnDraw`. Remplacez `OnPrint` pour exécuter un rendu qui doit être effectué uniquement lors de l'impression et pas pour l'affichage à l'écran. Par exemple, pour imprimer des en-têtes ou des pieds (voir l’article [Headers and Footers](../mfc/headers-and-footers.md) pour plus d’informations). Ensuite, appelez `OnDraw` de la substitution de `OnPrint` pour effectuer les opérations communes au rendu à l'écran et à l'impression.

Le fait que `OnDraw` génère l'affichage à la fois à l'écran et à l'impression, signifie que votre application est WYSIWYG : "What you see is what you get (vous obtenez ce que vous voyez)". Toutefois, supposons que vous ne développiez pas une application WYSIWYG. Par exemple, prenez le cas d'un éditeur de texte qui utilise une police en gras pour l'impression mais affiche des codes de contrôle pour indiquer le texte en gras sur l'écran. Dans ce type de situation, vous utilisez `OnDraw` strictement pour l'écran. Lorsque vous remplacez `OnPrint`, remplacez l'appel à `OnDraw` par un appel à une fonction de dessin distincte. La fonction dessine le document de la manière dont il apparaît sur le papier, à l'aide des attributs que vous n'affichez pas sur l'écran.

## <a name="printer-pages-vs-document-pages"></a><a name="_core_printer_pages_vs.._document_pages"></a>Pages d’imprimante vs Pages de documents

Lorsque vous faites référence à des numéros de page, il est parfois nécessaire de distinguer le concept de page dans le cadre de l'imprimante et le concept de page dans le cadre d'un document. Du point de vue de l'imprimante, une page est une feuille de papier. Toutefois, une feuille de papier n'est pas nécessairement une page du document. Par exemple, si vous imprimez un bulletin d’informations, où les feuilles doivent être pliées, une feuille de papier peut contenir les première et dernière pages du document, côte à côte. De même, si vous imprimez une feuille de calcul, le document ne comprend pas les pages du tout. En revanche, une feuille de papier peut contenir des lignes allant de 1 à 20 et des colonnes de 6 à 10.

Tous les numéros de page de la structure [CPrintInfo](../mfc/reference/cprintinfo-structure.md) se réfèrent aux pages d’imprimante. Le framework appelle `OnPrepareDC` et `OnPrint` une fois pour chaque feuille de papier qui transite par l'imprimante. Lorsque vous remplacez la fonction [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) pour spécifier la durée du document, vous devez utiliser les pages d’imprimante. Si une correspondance un-à-un est possible (autrement dit, une page d'impression est égale à une page de document), alors le processus est simplifié. Si, en revanche, les pages de documents et d'impression ne correspondent pas directement, vous devez les convertir entre elles. Par exemple, envisagez d'imprimer une feuille de calcul. En remplaçant `OnPreparePrinting`, vous devez calculer le nombre de feuilles de papier nécessaires pour imprimer la feuille de calcul entière, puis utiliser cette valeur en appelant la fonction membre `SetMaxPage` de `CPrintInfo`. De même, lorsque `OnPrepareDC`vous l’emportez, vous devez traduire *m_nCurPage* dans la gamme de lignes et de colonnes qui apparaîtront sur cette feuille particulière, puis ajuster l’origine viewport en conséquence.

## <a name="print-time-pagination"></a><a name="_core_print.2d.time_pagination"></a>Imprimer-Temps Pagination

Dans certains cas, il est possible que votre classe d'affichage ne connaisse pas à l'avance la longueur du document avant qu'il soit réellement imprimé. Par exemple, supposons que votre application n'est pas WYSIWYG, donc la longueur d'un document à l'écran ne correspond pas à sa longueur une fois imprimée.

Cela pose un problème lorsque vous remplacez [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) pour votre classe de `SetMaxPage` vue: vous ne pouvez pas passer une valeur à la fonction de la structure [CPrintInfo,](../mfc/reference/cprintinfo-structure.md) parce que vous ne connaissez pas la longueur d’un document. Si l'utilisateur ne spécifie pas un numéro de page pour arrêter d'utiliser la boîte de dialogue Imprimer, le framework ne saura pas quand arrêter la boucle d'impression. La seule façon de déterminer l'arrêt de la boucle d'impression est d'imprimer le document et de voir à quel moment il se termine. La classe d'affichage doit vérifier la fin du document lorsqu'il est imprimé, puis d'avertir le framework lorsque la fin est atteinte.

Le cadre repose sur la fonction [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) de votre classe de vue pour lui dire quand s’arrêter. Après chaque `OnPrepareDC`appel à , le `CPrintInfo` cadre vérifie un membre de la structure appelée *m_bContinuePrinting*. Sa valeur par défaut est **VRAI.** Dès lors qu'elle reste inchangée, le framework poursuit la boucle d'impression. S’il est réglé sur **FALSE**, le cadre s’arrête. Pour effectuer la pagination à `OnPrepareDC` temps d’impression, remplacez-vous pour vérifier si la fin du document a été atteinte et *définissez m_bContinuePrinting* à **FALSE** lorsqu’il l’a fait.

La mise `OnPrepareDC` en œuvre par défaut des ensembles *m_bContinuePrinting* à **FALSE** si la page actuelle est supérieure à 1. Cela signifie que si la longueur du document n'est pas spécifiée, le framework suppose que le document ne comporte qu'une seule page. La conséquence de ce fait est que vous devez être prudent lorsque vous appelez la version de la classe de base de `OnPrepareDC`. Ne présumez pas que *m_bContinuePrinting* sera **VRAI** après avoir appelé la version de classe de base.

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [En-têtes et pieds](../mfc/headers-and-footers.md)

- [Répartition des ressources GDI](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Voir aussi

[Impression](../mfc/printing.md)<br/>
[Classe CView](../mfc/reference/cview-class.md)<br/>
[Classe CDC](../mfc/reference/cdc-class.md)
