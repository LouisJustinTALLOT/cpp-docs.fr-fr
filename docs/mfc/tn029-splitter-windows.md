---
title: 'TN029 : Fenêtres fractionnées | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.windows.splitter
dev_langs:
- C++
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f0419e8f8aea141c3aaa54e320200160dae877f
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957222"
---
# <a name="tn029-splitter-windows"></a>TN029 : fenêtres fractionnées
Cette note décrit les classes MFC [CSplitterWnd classe](../mfc/reference/csplitterwnd-class.md), qui fournit la fenêtre fractionne et gère le redimensionnement des autres fenêtres de volet.  
  
## <a name="splitter-styles"></a>Styles de séparateur  
 A `CSplitterWnd` prend en charge deux différents styles de fractionnement de windows.  
  
 Dans « séparateurs statiques », la fenêtre fractionnée crée les volets lors de sa création. L’ordre et le nombre de volets ne changent jamais. Barres de fractionnement sont utilisées pour redimensionner les volets différents. Vous pouvez utiliser ce style pour afficher une classe d’affichage différente dans chaque volet. L’éditeur d’images Visual C++ et le Gestionnaire de fichiers Windows sont des exemples de programmes qui utilisent ce style de séparateur. Ce style de fenêtre fractionnée n’utilise pas de zones de séparateur.  
  
 Dans « séparateurs dynamiques », les volets supplémentaires sont créés et détruits en tant qu’utilisateur divisions et un partage nouvelles vues. Ce séparateur commence par une vue unique et fournit des zones de fractionnement de l’utilisateur lancer le fractionnement. La fenêtre fractionnée crée dynamiquement un nouvel objet de vue lorsque la vue est fractionnée dans un seul sens. Ce nouvel objet de vue représente le nouveau volet. Si la vue est fractionnée dans deux directions à l’aide de l’interface de clavier, la fenêtre fractionnée crée trois nouveaux objets de vue pour les trois volets de nouveau. Pendant que le fractionnement est actif, Windows affiche la boîte de fractionnement en tant qu’une barre de fractionnement entre les volets. Windows détruit les objets de vue lorsque l’utilisateur supprime une division, mais le reste de vue d’origine jusqu'à ce que la fenêtre fractionnée lui-même est détruit. Microsoft Excel et Microsoft Word sont des exemples d’applications qui utilisent le style fractionnées dynamiques.  
  
 Lorsque vous créez un type de fenêtre fractionnée, vous devez spécifier le nombre maximal de lignes et colonnes qui gère le séparateur. Un séparateur statique créera des volets pour remplir les lignes et les colonnes. Un séparateur dynamique créera uniquement le premier volet lorsque le `CSplitterWnd` est créé.  
  
 Le nombre maximal de volets, que vous pouvez spécifier pour les fenêtres fractionnées statiques est 16 lignes par 16 colonnes. Les configurations recommandées sont :  
  
-   colonnes de la 1 ligne x 2 : généralement avec les différents volets  
  
-   colonne de 2 lignes x 1 : généralement avec les différents volets  
  
-   les colonnes 2 lignes x 2 : généralement avec les volets semblables  
  
 Le nombre maximal de volets que vous pouvez spécifier pour les fenêtres fractionnées dynamiques est de 2 lignes sur 2 colonnes. Les configurations recommandées sont :  
  
-   colonnes de la 1 ligne x 2 : pour les données en colonnes  
  
-   colonne de 2 lignes x 1 : pour les données textuelles ou autres  
  
-   les colonnes 2 lignes x 2 : grille ou une table orientée données  
  
## <a name="splitter-examples"></a>Exemples de fractionnement  
 La plupart des exemples de programmes MFC utilisent des fenêtres fractionnées directement ou indirectement. L’exemple général MFC [VIEWEX](../visual-cpp-samples.md) illustre plusieurs utilisations de fenêtres fractionnées statiques, y compris comment placer un séparateur dans un séparateur.  
  
 Vous pouvez également utiliser ClassWizard pour créer une nouvelle classe interface multidocument (MDI) enfant frame fenêtre qui contient une fenêtre fractionnée. Pour plus d’informations sur les fenêtres fractionnées, consultez [plusieurs Types de documents, vues et fenêtres Frame](../mfc/multiple-document-types-views-and-frame-windows.md).  
  
## <a name="terminology-used-by-implementation"></a>Terminologie utilisée par l’implémentation  
 Voici une liste de termes qui sont spécifiques aux fenêtres fractionnées :  
  
 `CSplitterWnd`:  
 Une fenêtre qui fournit des contrôles de volet de fractionnement et de barres de défilement qui sont partagées entre tous les volets sur une ligne ou colonne. Vous spécifiez des lignes et des colonnes avec des numéros de base zéro (le premier volet est ligne = 0 et colonne = 0).  
  
 Volet :  
 Une fenêtre d’application spécifique qui un `CSplitterWnd` gère. Un volet est généralement un objet qui est dérivé de la [classe CView](../mfc/reference/cview-class.md), mais peut être une [CWnd](../mfc/reference/cwnd-class.md) objet ayant l’ID de fenêtre enfant approprié.  
  
 Pour utiliser un `CWnd`-dérivée d’objet, passez le RUNTIME_CLASS de l’objet à la `CreateView` fonctionnent comme vous le feriez si vous utilisiez un `CView`-classe dérivée. Votre classe doit utiliser DECLARE_DYNCREATE et IMPLEMENT_DYNCREATE, car l’infrastructure utilise la création dynamique lors de l’exécution. Bien qu’il y a beaucoup de code dans `CSplitterWnd` qui est spécifique à la `CView` (classe), [CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) est toujours utilisé avant que ces actions sont effectuées.  
  
 Barre de fractionnement :  
 Un contrôle qui est placé entre les lignes et colonnes de volets. Il peut être utilisé pour ajuster les tailles des lignes ou colonnes de volets.  
  
 Boîte de fractionnement :  
 Un contrôle dans un dynamique `CSplitterWnd` que vous pouvez utiliser pour créer de nouvelles lignes ou colonnes de volets. Il se trouve en haut de la barre de défilement verticale ou à gauche des barres de défilement horizontale.  
  
 Intersection de fractionnement :  
 L’intersection d’une barre de fractionnement vertical et une barre de fractionnement horizontal. Vous pouvez le faire glisser pour ajuster la taille d’une ligne et la colonne de volets simultanément.  
  
## <a name="shared-scroll-bars"></a>Les barres de défilement partagé  
 La `CSplitterWnd` classe prend également en charge les barres de défilement partagé. Ces contrôles de barre de défilement sont des enfants de le `CSplitterWnd` et sont partagés avec les différents volets de séparateur.  
  
 Par exemple, dans une fenêtre de la colonne 1, ligne x 2, vous pouvez spécifier WS_VSCROLL lors de la création du `CSplitterWnd`. Windows crée un contrôle de barre de défilement spécial qui est partagé entre les deux volets.  
  
```  
[      ][      ][^]  
[pane00][pane01][|]  
[      ][      ][v]  
```  
  
 Lorsque l’utilisateur déplace la barre de défilement, vous recevrez les messages WM_VSCROLL pour les deux vues. Lorsque des affichages définit la position de barre de défilement, la barre de défilement partagé sera définie.  
  
 Notez que les barres de défilement partagé sont particulièrement utiles avec les objets de vue similaire. Si vous combinez des vues de types différents dans un séparateur, vous devez écrire un code spécial pour coordonner les positions de défilement. N’importe quel `CView`-classe dérivée qui utilise le `CWnd` API délègue à la barre de défilement partagé s’il existe de barre de défilement. Le `CScrollView` implémentation est un exemple d’un `CView` classe qui prend en charge partagé des barres de défilement. Les classes qui ne sont pas dérivés de `CView`, des classes qui s’appuient sur les barres de défilement du contrôle de code non, ou qui utilisent des infrastructures Windows standard (par exemple, `CEditView`) ne fonctionne pas avec la fonctionnalité de barre de défilement partagé de `CSplitterWnd`.  
  
## <a name="minimum-sizes"></a>Tailles minimales  
 Pour chaque ligne, il existe une hauteur de ligne minimale, et pour chaque colonne a une largeur minimale de la colonne. Ce minimum garantit qu’un volet n’est pas trop petit pour être affichées en détail.  
  
 Pour une fenêtre fractionnée statique, la largeur de colonnes et la hauteur minimale de ligne initiale est 0. Pour une fenêtre fractionnée dynamique, la largeur de colonnes et la hauteur minimale des lignes initiales sont définis par le *sizeMin* paramètre de la `CSplitterWnd::Create` (fonction).  
  
 Vous pouvez modifier ces tailles minimales en utilisant le [CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo) et [CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo) fonctions.  
  
## <a name="actual-vs-ideal-sizes"></a>Vs réels. Taille idéale  
 La disposition des volets dans la fenêtre fractionnée dépend de la taille de l’image qui les contient. Lorsqu’un utilisateur redimensionne le frame contenant, le `CSplitterWnd` repositionne et redimensionne les volets afin qu’elles tiennent ainsi que possible.  
  
 L’utilisateur peut définir manuellement la ligne de tailles de largeur des colonnes et la hauteur, ou le programme peut définir la taille idéale en utilisant la `CSplitterWnd` classe. La taille réelle peut être inférieure ou supérieure à la solution idéale. Windows s’ajuste à la taille réelle si il n’est pas assez de place pour afficher la taille idéale ou s’il existe trop d’espace vide à droite ou en bas de la fenêtre fractionnée.  
  
## <a name="custom-controls"></a>Contrôles personnalisés  
 Vous pouvez remplacer de nombreuses fonctions pour fournir un comportement personnalisé et une interface personnalisée. Vous pouvez remplacer ce premier ensemble pour fournir des images de remplacement pour les différents composants de graphiques d’une fenêtre fractionnée.  
  
- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`  
  
- `virtual void OnInvertTracker(const CRect& rect);`  
  
 Vous appelez cette fonction pour créer un contrôle de barre de défilement partagé. Vous pouvez substituer pour créer des contrôles supplémentaires en regard de la barre de défilement.  
  
- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`  
  
 Ces fonctions implémentent la logique de la fenêtre fractionnée dynamique. Vous pouvez remplacer pour fournir la logique de fractionnement plus avancée.  
  
- `virtual void DeleteView(int row, int col);`  
  
- `virtual BOOL SplitRow(int cyBefore);`  
  
- `virtual BOOL SplitColumn(int cxBefore);`  
  
- `virtual void DeleteRow(int rowDelete);`  
  
- `virtual void DeleteColumn(int colDelete);`  
  
## <a name="cview-functionality"></a>Fonctionnalités de CView  
 Le `CView` classe utilise les commandes suivantes de haut niveau de déléguer à la `CSplitterWnd` implémentation. Étant donné que ces commandes sont virtuelles, la norme `CView` implémentation ne nécessite pas l’ensemble de le `CSplitterWnd` pour être liée à l’implémentation. Pour les applications qui utilisent `CView` mais pas `CSplitterWnd`, le `CSplitterWnd` implémentation ne sera pas liée à l’application.  
  
 `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`  
 Vérifie si ID_NEXT_PANE ou ID_PREV_PANE est actuellement possible.  
  
 `virtual void ActivateNext(BOOL bPrev = FALSE);`  
 Exécute la commande « Suivant volet » ou « précédent ».  
  
 `virtual BOOL DoKeyboardSplit();`  
 Exécute la commande, généralement « fenêtre fractionner » de fractionnement via le clavier.  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

