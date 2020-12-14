---
description: 'En savoir plus sur : TN014 : contrôles personnalisés'
title: 'TN014 : contrôles personnalisés'
ms.date: 06/28/2018
f1_keywords:
- vc.controls
helpviewer_keywords:
- TN014
- custom controls [MFC]
ms.assetid: 1917a498-f643-457c-b570-9a0af7dbf7bb
ms.openlocfilehash: c9b069e0101b279558c5bcd4ffb7f457120e8187
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215974"
---
# <a name="tn014-custom-controls"></a>TN014 : contrôles personnalisés

Cette note décrit la prise en charge MFC pour les contrôles personnalisés et de dessin automatique. Il décrit également le sous-classement dynamique et décrit la relation entre les objets [CWnd](../mfc/reference/cwnd-class.md) et les `HWND` .

L'exemple d'application CTRLTEST MFC montre comment utiliser de nombreux contrôles personnalisés. Consultez le code source de l’exemple général MFC [CTRLTEST](../overview/visual-cpp-samples.md) et l’aide en ligne.

## <a name="owner-draw-controlsmenus"></a>Contrôles/menus en mode owner-draw

Windows prend en charge les contrôles et les menus en mode owner-draw à l'aide des messages Windows. La fenêtre parente de n'importe quel contrôle ou menu reçoit ces messages et appelle des fonctions en réponse. Vous pouvez remplacer ces fonctions pour personnaliser l'aspect visuel et le comportement du contrôle ou du menu owner-draw.

MFC gère directement le mode owner-draw avec les fonctions suivantes :

- [CWnd::OnDrawItem](../mfc/reference/cwnd-class.md#ondrawitem)

- [CWnd::OnMeasureItem](../mfc/reference/cwnd-class.md#onmeasureitem)

- [CWnd::OnCompareItem](../mfc/reference/cwnd-class.md#oncompareitem)

- [CWnd::OnDeleteItem](../mfc/reference/cwnd-class.md#ondeleteitem)

Il vous est possible de remplacer ces fonctions dans votre classe dérivée `CWnd` pour implémenter le comportement de dessin personnalisé.

Cette approche ne mène pas à du code réutilisable. Si vous avez deux contrôles similaires dans deux différentes classes `CWnd`, vous devez implémenter le comportement du contrôle personnalisé à deux emplacements. L'architecture du contrôle de dessin automatique compatible MFC résoud ce problème.

## <a name="self-draw-controls-and-menus"></a>Contrôles et menus de dessin automatique

MFC fournit une implémentation par défaut (dans les `CWnd` classes et [CMenu](../mfc/reference/cmenu-class.md) ) pour les messages owner-draw standard. Cette implémentation par défaut décode les paramètres owner-draw et délègue les messages owner-draw aux contrôles ou menus. Il est question de dessin automatique car le code de dessin se trouve dans la classe du contrôle ou du menu, et non dans la fenêtre propriétaire.

En utilisant les contrôles de dessin automatique vous pouvez générer des classes de contrôle réutilisables qui utilisent la sémantique owner-draw pour afficher le contrôle. Le code pour dessiner le contrôle figure dans la classe de contrôle, et non son parent. Il s'agit d'une approche orientée objet de programmation de contrôle personnalisé. Ajoutez la liste de fonctions suivante à vos classes de dessin automatique :

- Pour les boutons de dessin automatique :

    ```cpp
    CButton:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw this button
    ```

- Pour les champs de dessin automatique :

    ```cpp
    CMenu:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this menu
    CMenu:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this menu
    ```

- Pour les zones de liste de dessin automatique :

    ```cpp
    CListBox:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this list box
    CListBox:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this list box

    CListBox:CompareItem(LPCOMPAREITEMSTRUCT);
    // insert code to compare two items in this list box if LBS_SORT
    CListBox:DeleteItem(LPDELETEITEMSTRUCT);
    // insert code to delete an item from this list box
    ```

- Pour les zones de liste déroulante de dessin automatique :

    ```cpp
    CComboBox:MeasureItem(LPMEASUREITEMSTRUCT);
    // insert code to measure the size of an item in this combo box
    CComboBox:DrawItem(LPDRAWITEMSTRUCT);
    // insert code to draw an item in this combo box

    CComboBox:CompareItem(LPCOMPAREITEMSTRUCT);
    // insert code to compare two items in this combo box if CBS_SORT
    CComboBox:DeleteItem(LPDELETEITEMSTRUCT);
    // insert code to delete an item from this combo box
    ```

Pour plus d’informations sur les structures owner-draw ([drawitemstruct,](/windows/win32/api/winuser/ns-winuser-drawitemstruct), [measureitemstruct,](/windows/win32/api/winuser/ns-winuser-measureitemstruct), [compareitemstruct,](/windows/win32/api/winuser/ns-winuser-compareitemstruct)et [deleteitemstruct,](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)), consultez la documentation MFC pour `CWnd::OnDrawItem` ,, et, `CWnd::OnMeasureItem` `CWnd::OnCompareItem` `CWnd::OnDeleteItem` respectivement.

## <a name="using-self-draw-controls-and-menus"></a>Utilisation des contrôles et menus de dessin automatique

Pour les champs de dessin automatique, vous devez substituer les méthodes `OnMeasureItem` et `OnDrawItem`.

Pour les zones de liste et les zones de liste déroulante de dessin automatique, vous devez remplacer `OnMeasureItem` et `OnDrawItem`. Vous devez spécifier le style de LBS_OWNERDRAWVARIABLE pour les zones de liste ou le style de CBS_OWNERDRAWVARIABLE pour les zones de liste déroulante dans le modèle de boîte de dialogue. Le style OWNERDRAWFIXED ne fonctionne pas avec les éléments de dessin automatique, car la hauteur d’élément fixe est déterminée avant que les contrôles de dessin automatique soient attachés à la zone de liste. (Vous pouvez utiliser les méthodes [CListBox :: SetItemHeight](../mfc/reference/clistbox-class.md#setitemheight) et [CComboBox :: SetItemHeight](../mfc/reference/ccombobox-class.md#setitemheight) pour surmonter cette limitation.)

Le passage à un style OWNERDRAWVARIABLE force le système à appliquer le style NOINTEGRALHEIGHT au contrôle. Étant donné que le contrôle ne peut pas calculer une hauteur intégrale avec des éléments de taille variable, le style par défaut de INTEGRALHEIGHT est ignoré et le contrôle est toujours NOINTEGRALHEIGHT. Si les éléments sont à hauteur fixe, vous pouvez empêcher les éléments partiels d'être dessinés en spécifiant que la taille de contrôle soit un multiplicateur entier de la taille d'élément.

Pour les zones de liste et les zones de liste déroulante à dessin automatique avec le style LBS_SORT ou CBS_SORT, vous devez substituer la `OnCompareItem` méthode.

Pour les zones de liste et les zones de liste déroulante de dessin automatique, `OnDeleteItem` n'est généralement pas remplacé. Vous pouvez remplacer `OnDeleteItem` si vous souhaitez effectuer un traitement spécial. Un cas où cela s'appliquerait lorsque la mémoire ou d'autres ressources sont stockées avec chaque élément de la zone de liste ou de la zone de liste déroulante.

## <a name="examples-of-self-drawing-controls-and-menus"></a>Exemples de contrôles et de menus de dessin automatique

L’exemple général de MFC [CTRLTEST](../overview/visual-cpp-samples.md) fournit des exemples d’un menu de dessin automatique et d’une zone de liste de dessin automatique.

L'exemple le plus typique d'un bouton de dessin automatique est un bouton bitmap. Un bouton bitmap est un bouton qui affiche une, deux ou trois images bitmap pour les différents états. Un exemple est fourni dans la classe MFC [CBitmapButton](../mfc/reference/cbitmapbutton-class.md).

## <a name="dynamic-subclassing"></a>Sous-classement dynamique

Occasionnellement, vous souhaiterez modifier la fonctionnalité d'objet qui existe déjà. Les exemples précédents requièrent que vous personnalisiez les contrôles avant qu'ils soient créés. Le sous-classement dynamique permet de personnaliser un contrôle qui a déjà été créé.

Le sous-classing est le terme Windows permettant de remplacer le <xref:System.Windows.Forms.Control.WndProc%2A> d’une fenêtre par un personnalisé `WndProc` et d’appeler l’ancien `WndProc` pour les fonctionnalités par défaut.

Cela ne doit pas être confondu avec la dérivation de classe C++. Pour clarifier, la classe de *base* des termes C++ et la *classe dérivée* sont analogues à la *superclasse* et à la sous- *classe* dans le modèle d’objet Windows. La dérivation C++ MFC et le sous-classement Windows sont fonctionnellement similaires, à moins que C++ ne prenne pas en charge le sous-classement dynamique.

La classe `CWnd` fournit la connexion entre un objet C++ (dérivé de `CWnd`) et un objet fenêtre Windows (appelé `HWND`).

Trois façons courantes permettent de les lier :

- `CWnd` crée `HWND`. Vous pouvez modifier le comportement dans une classe dérivée en créant une classe dérivée de `CWnd`. Le `HWND` est créé lorsque votre application appelle [CWnd :: Create](../mfc/reference/cwnd-class.md#create).

- L'application joint `CWnd` à un objet `HWND`existant. Le comportement de la fenêtre existante n'est pas modifié. Il s’agit d’un cas de délégation qui est rendu possible en appelant [CWnd :: Attach pour ajouter](../mfc/reference/cwnd-class.md#attach) un alias à `HWND` un `CWnd` objet existant.

- `CWnd` est attaché à un `HWND` existant et il vous est possible de modifier le comportement dans une classe dérivée. On parle sous-classement dynamique car nous modifions le comportement, par conséquent la classe, de l'objet Windows au moment de l'exécution.

Vous pouvez obtenir un sous-ordre dynamique à l’aide des méthodes [CWnd :: SubclassWindow](../mfc/reference/cwnd-class.md#subclasswindow) et[CWnd :: SubclassDlgItem](../mfc/reference/cwnd-class.md#subclassdlgitem).

Les deux routines joignent un objet `CWnd` au `HWND` existant. `SubclassWindow` prend le `HWND` directement. `SubclassDlgItem` est une fonction d'assistance qui accepte un ID de contrôle et la fenêtre parente. `SubclassDlgItem` est conçu pour joindre des objets C++ aux contrôles de la boîte de dialogue créée à partir d'un modèle de boîte de dialogue.

Consultez l’exemple [CTRLTEST](../overview/visual-cpp-samples.md) pour obtenir plusieurs exemples d’utilisation de `SubclassWindow` et de `SubclassDlgItem` .

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
