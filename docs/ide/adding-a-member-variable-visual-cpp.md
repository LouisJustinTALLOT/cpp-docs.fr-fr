---
title: Ajouter une variable membre
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.variable
- vc.codewiz.variable.overview
helpviewer_keywords:
- member variables, adding
- member variables
- add member variable wizard [C++]
- dialog box controls, member variables
- dialog box controls, variable types
- variables, dialog box control member variables
ms.assetid: 437783bd-8eb4-4508-8b73-7380116e9d71
ms.openlocfilehash: 2a519c0606a7df6e0ce55997a055d78865afafbf
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694411"
---
# <a name="add-a-member-variable"></a>Ajouter une variable membre

Vous pouvez ajouter une variable membre à une classe à l’aide d’Affichage de classes. Les variables membres peuvent être utilisées pour [l’échange et la validation de données](../mfc/dialog-data-exchange-and-validation.md), ou elles peuvent être génériques. L’Assistant Ajout de variable membre est conçu pour prélever les informations importantes et les utiliser pour insérer des éléments dans vos fichiers sources aux emplacements appropriés. Vous pouvez ajouter une variable membre à partir de l’[Éditeur de boîtes de dialogue](../windows/dialog-editor.md) dans [Affichage des ressources](../windows/resource-view-window.md), ou à partir d’[Affichage de classes](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
> Quand vous concevez et implémentez une boîte de dialogue, il peut être plus efficace d’utiliser l’Éditeur de boîtes de dialogue pour ajouter les contrôles de boîte de dialogue, puis d’implémenter les variables membres des contrôles.

**Pour ajouter une variable membre pour un contrôle de boîte de dialogue dans l’affichage des ressources à l’aide de l’Assistant Ajout de variable membre**

1. Dans l’affichage des ressources, développez le nœud du projet et le nœud Boîte de dialogue pour afficher la liste des boîtes de dialogue du projet.

1. Double-cliquez sur la boîte de dialogue à laquelle vous souhaitez ajouter la variable membre pour l’ouvrir dans l’Éditeur de boîtes de dialogue.

1. Dans la boîte de dialogue affichée dans l’Éditeur de boîtes de dialogue, cliquez avec le bouton droit sur le contrôle auquel vous souhaitez ajouter la variable membre.

1. Dans le menu contextuel, choisissez **Ajouter une variable** pour afficher l’[Assistant Ajout de variable membre](#add-member-variable-wizard).

   > [!NOTE]
   > Une valeur par défaut vous est déjà proposée dans **ID de contrôle**.

1. Indiquez les informations nécessaires dans les zones appropriées de l’Assistant. Pour plus d’informations, consultez [Contrôles de boîtes de dialogue et types de variables](#dialog-box-controls-and-variable-types).

1. Sélectionnez **Terminer** pour ajouter la définition et le code d’implémentation au projet et fermer l’Assistant.

**Pour ajouter une variable membre à partir d’Affichage de classes à l’aide de l’Assistant Ajout de variable membre**

1. Dans [l’affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), développez le nœud du projet afin d’afficher ses classes.

1. Cliquez avec le bouton droit sur la classe à laquelle vous souhaitez ajouter une variable.

1. Dans le menu contextuel, choisissez **Ajouter**, puis **Ajouter une variable** pour afficher l’Assistant Ajout de variable membre.

1. Indiquez les informations nécessaires dans les zones appropriées de l’Assistant. Pour plus d’informations, consultez [Assistant Ajout de variable membre](#add-member-variable-wizard).

1. Sélectionnez **Terminer** pour ajouter la définition et le code d’implémentation au projet et fermer l’Assistant.

## <a name="in-this-section"></a>Dans cette section

- [Assistant Ajout de variable membre](#add-member-variable-wizard)
- [Contrôles de boîtes de dialogue et types de variables](#dialog-box-controls-and-variable-types)

## <a name="add-member-variable-wizard"></a>Assistant Ajout de variable membre

Cet Assistant ajoute une déclaration de variable membre au fichier d’en-tête. En fonction des options, elle peut ajouter le code au fichier .cpp. Une fois que vous avez ajouté la variable membre avec l’Assistant, vous pouvez modifier le code dans l’environnement de développement.

- **Accès**

  Définit l’accès à la variable membre. Les modificateurs d’accès sont des mots clés spécifiant l’accès des autres classes à la variable membre. Pour plus d’informations sur la spécification de l’accès, consultez [Contrôle d’accès aux membres](../cpp/member-access-control-cpp.md). Le niveau d’accès à la variable membre est défini par défaut sur `public`.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

- **Type de variable**

  Définit le type de retour pour la variable de membre que vous ajoutez.

  - Si vous ajoutez une variable membre qui n’est pas un contrôle de boîte de dialogue, sélectionnez dans la liste des types disponibles.

    Pour plus d’informations sur les types, consultez [Types fondamentaux](../cpp/fundamental-types-cpp.md).

    |||
    |-|-|
    |`char`|`short`|
    |`double`|`unsigned char`|
    |`float`|`unsigned int`|
    |`int`|`unsigned long`|
    |`long`||

  - Si vous ajoutez une variable membre pour un contrôle de boîte de dialogue, cette zone est renseignée avec le type de l’objet retourné pour un contrôle ou une valeur. Si vous sélectionnez **Contrôle**, **Type de variable** spécifie la classe de base du contrôle que vous sélectionnez dans la zone **ID de contrôle**. Si le contrôle de boîte de dialogue peut contenir une valeur et si vous sélectionnez **Valeur**, **Type de variable** spécifie le type approprié pour la valeur que le contrôle peut contenir. Pour plus d’informations, consultez [Contrôles de boîtes de dialogue et types de variables](#dialog-box-controls-and-variable-types).

    Cette valeur dépend de la sélection dans **ID de contrôle** et ne peut pas être modifiée.

- **Nom de la variable**

  Définit le nom de la variable membre que vous ajoutez. Les variables membres commencent généralement par la chaîne d’identification `m_`, qui vous est fournie par défaut.

- **Variable de contrôle**

  Indique que la variable membre gère un contrôle dans une boîte de dialogue avec prise en charge de [l’échange de données et de la validation des données](../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations, consultez [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange). Cette option est disponible seulement pour les variables membres ajoutées à des classes dérivées de [CDialog](../mfc/reference/cdialog-class.md). Cochez cette case pour activer les options **ID de contrôle** et **Type de contrôle**.

- **ID de contrôle**

  Définit l’ID pour la variable de contrôle que vous ajoutez. Dans la liste, sélectionnez l’ID pour le type de contrôle pour lequel vous ajoutez la variable membre. La liste est active seulement quand la case **Variable de contrôle** est cochée, et elle est limité aux ID des contrôles déjà ajoutés à la boîte de dialogue. Par exemple, pour le bouton **OK** standard, l’ID de contrôle est **IDOK**.

  |Option|Description|
  |------------|-----------------|
  |**Contrôle**|Cette option est définie par défaut pour le type de contrôle. Elle gère le contrôle lui-même, et non l’état ou le contenu du contrôle (comme vous pourriez vouloir le faire avec une zone de liste, une zone de liste modifiable ou une zone d’édition).|
  |**Valeur**|Cette option est disponible pour les types de contrôle qui peuvent contenir une valeur ou afficher un état, par exemple une zone d’édition ou une case à cocher. Elle est également disponible pour les types de contrôle pour lesquels vous pouvez gérer la plage, le contenu ou l’état. Pour plus d’informations, consultez [Contrôles de boîtes de dialogue et types de variables](#dialog-box-controls-and-variable-types).|

- **Catégorie**

  Spécifie si la variable est basée sur un type de contrôle ou sur la valeur du contrôle.

- **Type de contrôle**

  Définit le type de contrôle ajouté. Vous ne pouvez pas changer cette case. Par exemple, un bouton a le type de contrôle **BUTTON** et une zone de liste modifiable a le type de contrôle **COMBOBOX**. Pour plus d’informations, consultez [Contrôles de boîtes de dialogue et types de variables](#dialog-box-controls-and-variable-types).

- **Nombre maximal de caractères**

  Disponible seulement quand **Type de Variable** est défini sur [CString](../atl-mfc-shared/reference/cstringt-class.md). Indique le nombre maximal de caractères que le contrôle peut contenir.

- **Valeur minimale**

  Disponible uniquement quand le type de variable est `BOOL`, `int`, `UINT`, `long`, `DWORD`, `float`, `double`, `BYTE`, `short`, [COLECurrency](../mfc/reference/colecurrency-class.md) ou [CTime](../atl-mfc-shared/reference/ctime-class.md). Indique la plus petite valeur acceptable pour une plage de mise à l’échelle ou de dates.

- **Valeur maximale**

  Disponible uniquement quand le type de variable est `BOOL`, `int`, `UINT`, `long`, `DWORD`, `float`, `double`, `BYTE`, `short`, `COLECurrency` ou `CTime`. Indique la plus haute valeur acceptable pour une plage de mise à l’échelle ou de dates.

- **Fichier .h**

  Pour les contrôles ActiveX, dont les variables membres nécessitent une classe wrapper. Définit le nom du fichier d’en-tête pour ajouter la déclaration de classe.

- **Fichier .cpp**

  Pour les contrôles ActiveX, dont les variables membres nécessitent une classe wrapper. Définit le nom du fichier d’implémentation pour ajouter la définition de classe.

- **Commentaire**

  Fournit un commentaire dans le fichier d’en-tête pour la variable membre.

## <a name="dialog-box-controls-and-variable-types"></a>Contrôles de boîtes de dialogue et types de variables

Vous pouvez utiliser l’[Assistant Ajout de variable membre](#add-member-variable-wizard) pour ajouter une variable membre à un contrôle de boîte de dialogue créé à l’aide de MFC. Le type de contrôle pour lequel vous ajoutez la variable membre détermine les options qui apparaissent dans la boîte de dialogue.

Le tableau suivant décrit tous les types de contrôles de boîtes de dialogue pris en charge dans MFC et dans l’[Éditeur de boîtes de dialogue](../windows/dialog-editor.md). Il montre également leurs types et valeurs disponibles.

|Contrôle|Type du contrôle|Type de variable de contrôle|Type de variable de valeur|Valeurs min/max (type valeur uniquement)|
|-------------|------------------|---------------------------|-------------------------|-----------------------------------------|
|Contrôle Animation|SysAnimate32|[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Bouton|BUTTON|[CButton](../mfc/reference/cbutton-class.md)|Aucun ; contrôle uniquement|N/A|
|Case à cocher|CHECK|[CButton](../mfc/reference/cbutton-class.md)|`BOOL`|Valeur min/Valeur max|
|Zone de liste modifiable|COMBOBOX|[CComboBox](../mfc/reference/ccombobox-class.md)|[CString](../atl-mfc-shared/reference/cstringt-class.md)|Nombre maximal de caractères|
|Contrôle Sélecteur de date et d’heure|SysDateTimePick32|[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)|[CTime](../atl-mfc-shared/reference/ctime-class.md)|Valeur min/Valeur max|
|Zone d’édition|EDITION|[CEdit](../mfc/reference/cedit-class.md)|`CString`, int, UINT, long, DWORD, float, double, BYTE, short, BOOL, `COleDateTime` ou `COleCurrency`|Valeur min/Valeur max ; certaines prennent en charge le nombre maximal de caractères|
|Contrôle de touche d’accès rapide|msctls_hotkey32|[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Zone de liste|LISTBOX|[CListBox](../mfc/reference/clistbox-class.md)|`CString`|Nombre maximal de caractères|
|Contrôle List|SysListView32|[CListCtrl](../mfc/reference/clistctrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Contrôle Month Calendar|SysMonthCal32|[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)|`CTime`|Valeur min/Valeur max|
|Contrôle Progress|msctls_progress32|[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Contrôle RichEdit 2|RichEdit20A|[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)|`CString`|Nombre maximal de caractères|
|Contrôle RichEdit|RICHEDIT|`CRichEditCtrl`|`CString`|Nombre maximal de caractères|
|Barre de défilement (verticale ou horizontale)|SCROLLBAR|[CScrollBar](../mfc/reference/cscrollbar-class.md)|`int`|Valeur min/Valeur max|
|Contrôle Slider|msctls_trackbar32|[CSliderCtrl](../mfc/reference/csliderctrl-class.md)|`int`|Valeur min/Valeur max|
|Contrôle Spin|msctls_updown32|[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Contrôle Tab|SysTabControl32|[CTabCtrl](../mfc/reference/ctabctrl-class.md)|Aucun ; contrôle uniquement|N/A|
|Contrôle Tree|SysTreeView32|[CTreeCtrl](../mfc/reference/ctreectrl-class.md)|Aucun ; contrôle uniquement|N/A|
