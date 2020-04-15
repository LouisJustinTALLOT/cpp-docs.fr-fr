---
title: CVSListBox, classe
ms.date: 11/19/2018
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
ms.openlocfilehash: 4ea48a263a01133419067979ee5fa3e62105c7f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373194"
---
# <a name="cvslistbox-class"></a>CVSListBox, classe

La `CVSListBox` classe prend en charge un contrôle de liste modifiable.

## <a name="syntax"></a>Syntaxe

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CVSListBox::CVSListBox](#cvslistbox)|Construit un objet `CVSListBox`.|
|`CVSListBox::~CVSListBox`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CVSListBox::AddItem](#additem)|Ajoute une chaîne à un contrôle de liste. (Substitue `CVSListBoxBase::AddItem`.)|
|[CVSListBox::EditItem](#edititem)|Démarre une opération de modification sur le texte d’un élément de contrôle de liste. (Substitue `CVSListBoxBase::EditItem`.)|
|[CVSListBox::GetCount](#getcount)|Récupère le nombre de chaînes dans un contrôle de liste modifiable. (Substitue `CVSListBoxBase::GetCount`.)|
|[CVSListBox::GetItemData](#getitemdata)|Récupère une valeur 32 bits spécifique à l’application qui est associée à un élément de contrôle de liste modifiable. (Substitue `CVSListBoxBase::GetItemData`.)|
|[CVSListBox::GetItemText](#getitemtext)|Récupère le texte d’un élément de contrôle de liste modifiable. (Substitue `CVSListBoxBase::GetItemText`.)|
|[CVSListBox::GetSelItem](#getselitem)|Récupère l’index zéro de l’élément actuellement sélectionné dans un contrôle de liste modifiable. (Substitue `CVSListBoxBase::GetSelItem`.)|
|`CVSListBox::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient envoyés aux [fonctions De Windows De TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Pour plus d’informations et de syntaxe méthode, voir [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitue `CVSListBoxBase::PreTranslateMessage`.)|
|[CVSListBox::RemoveItem](#removeitem)|Supprime un élément d’un contrôle de liste modifiable. (Substitue `CVSListBoxBase::RemoveItem`.)|
|[CVSListBox::SelectItem](#selectitem)|Sélectionne une chaîne de contrôle de liste modifiable. (Substitue `CVSListBoxBase::SelectItem`.)|
|[CVSListBox::SetItemData](#setitemdata)|Associe une valeur 32 bits spécifique à l’application avec un élément de contrôle de liste modifiable. (Substitue `CVSListBoxBase::SetItemData`.)|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|Retourne la poignée au contrôle de vue de liste intégré actuel.|

## <a name="remarks"></a>Notes

La `CVSListBox` classe fournit un ensemble de boutons d’édition qui permettent à l’utilisateur de créer, modifier, supprimer ou réorganiser les éléments dans un contrôle de liste.

Ce qui suit est une image du contrôle de liste modifiable. La deuxième liste d’entrée, qui s’intitule "Item2", est sélectionnée pour l’édition.

![Contrôle CVSListBox](../../mfc/reference/media/cvslistbox.png "Contrôle CVSListBox")

Si vous utilisez l’éditeur de ressources pour ajouter un contrôle de liste modifiable, notez que le volet **Toolbox** de l’éditeur ne fournit pas un contrôle de liste modifiable prédéfinis. Au lieu de cela, ajoutez un contrôle statique tel que le contrôle **de la boîte de groupe.** Le cadre utilise le contrôle statique en tant que placeholder pour spécifier la taille et la position du contrôle de liste modifiable.

Pour utiliser un contrôle de liste modifiable `CVSListBox` dans un modèle de boîte de dialogue, déclarez une variable dans votre classe de boîte de dialogue. Pour soutenir l’échange de données entre `DDX_Control` la variable `DoDataExchange` et le contrôle, définissez une entrée macro dans la méthode de la boîte de dialogue. Par défaut, le contrôle de liste modifiable est créé sans boutons de modification. Utilisez la méthode héritée CVSListBoxBase::SetStandardButtons pour activer les boutons de modification.

Pour plus d’informations, consultez `New Controls` le répertoire Échantillons, l’échantillon, les fichiers Page3.cpp et Page3.h.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxvslistbox.h

## <a name="cvslistboxadditem"></a><a name="additem"></a>CVSListBox::AddItem

Ajoute une chaîne à un contrôle de liste.

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*strIext strIext*<br/>
[dans] Une référence à une chaîne.

*dwData dwData*<br/>
[dans] Une valeur 32 bits spécifique à l’application qui est associée à la chaîne. La valeur par défaut est 0.

*iIndex (en)*<br/>
[dans] L’indice zéro de la position qui tiendra la chaîne. Si le *paramètre iIndex* est de -1, la chaîne est ajoutée à la fin de la liste. La valeur par défaut est -1.

### <a name="return-value"></a>Valeur de retour

L’indice zéro de la position de la chaîne dans le contrôle de liste.

### <a name="remarks"></a>Notes

Utilisez la méthode [CVSListBox::GetItemData](#getitemdata) pour récupérer la valeur spécifiée par le paramètre *dwData.* Cette valeur peut être un intégré spécifique à l’application ou un pointeur à d’autres données.

## <a name="cvslistboxcvslistbox"></a><a name="cvslistbox"></a>CVSListBox::CVSListBox

Construit un objet `CVSListBox`.

```
CVSListBox();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cvslistboxedititem"></a><a name="edititem"></a>CVSListBox::EditItem

Démarre une opération de modification sur le texte d’un élément de contrôle de liste.

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] Indice zéro d’un élément de contrôle de liste.

### <a name="return-value"></a>Valeur de retour

VRAI si l’opération de modification commence avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

L’utilisateur démarre une opération de modification soit en cliquant deux fois sur l’étiquette d’un élément, soit en appuyant sur la clé **F2** ou **SPACEBAR** lorsqu’un élément a la mise au point.

## <a name="cvslistboxgetcount"></a><a name="getcount"></a>CVSListBox::GetCount

Récupère le nombre de chaînes dans un contrôle de liste modifiable.

```
virtual int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments figurant dans le contrôle de liste.

### <a name="remarks"></a>Notes

Notez que le nombre est supérieur à la valeur indicative du dernier élément parce que l’indice est basé sur zéro.

## <a name="cvslistboxgetitemdata"></a><a name="getitemdata"></a>CVSListBox::GetItemData

Récupère une valeur 32 bits spécifique à l’application qui est associée à un élément de contrôle de liste modifiable.

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément de contrôle de liste modifiable.

### <a name="return-value"></a>Valeur de retour

La valeur 32 bits associée à l’élément spécifié.

### <a name="remarks"></a>Notes

Utilisez la [CVSListBox::SetItemData](#setitemdata) ou [CVSListBox::AddItem](#additem) méthode pour associer la valeur 32 bits avec l’élément de contrôle de liste. Cette valeur peut être un intégré spécifique à l’application ou un pointeur à d’autres données.

## <a name="cvslistboxgetitemtext"></a><a name="getitemtext"></a>CVSListBox::GetItemText

Récupère le texte d’un élément de contrôle de liste modifiable.

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément de contrôle de liste modifiable.

### <a name="return-value"></a>Valeur de retour

Un objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contient le texte de l’élément spécifié.

### <a name="remarks"></a>Notes

## <a name="cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a>CVSListBox::GetListHwnd

Retourne la poignée au contrôle de vue de liste intégré actuel.

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>Valeur de retour

Une poignée au contrôle de vue de liste intégré.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour récupérer une poignée au `CVSListBox` contrôle de vue de liste intégré qui prend en charge la classe.

## <a name="cvslistboxgetselitem"></a><a name="getselitem"></a>CVSListBox::GetSelItem

Récupère l’index zéro de l’élément actuellement sélectionné dans un contrôle de liste modifiable.

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>Valeur de retour

Si cette méthode est efficace, l’indice zéro de l’élément actuellement sélectionné; sinon, -1.

### <a name="remarks"></a>Notes

## <a name="cvslistboxremoveitem"></a><a name="removeitem"></a>CVSListBox::RemoveItem

Supprime un élément d’un contrôle de liste modifiable.

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément de contrôle de liste modifiable.

### <a name="return-value"></a>Valeur de retour

VRAI si l’élément spécifié est supprimé; autrement, FALSE.

### <a name="remarks"></a>Notes

## <a name="cvslistboxselectitem"></a><a name="selectitem"></a>CVSListBox::SelectItem

Sélectionne une chaîne de contrôle de liste modifiable.

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>Paramètres

*iItem*<br/>
[dans] L’index zéro d’un élément de contrôle de liste modifiable.

### <a name="return-value"></a>Valeur de retour

VRAI si cette méthode est réussie; autrement, FALSE.

### <a name="remarks"></a>Notes

Cette méthode sélectionne l’élément spécifié et, si elle est nécessaire, fait défiler l’élément en vue.

## <a name="cvslistboxsetitemdata"></a><a name="setitemdata"></a>CVSListBox::SetItemData

Associe une valeur 32 bits spécifique à l’application avec un élément de contrôle de liste modifiable.

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
[dans] L’index zéro d’un élément de contrôle de liste modifiable.

*dwData dwData*<br/>
[dans] Une valeur 32 bits. Cette valeur peut être un intégré spécifique à l’application ou un pointeur à d’autres données.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
