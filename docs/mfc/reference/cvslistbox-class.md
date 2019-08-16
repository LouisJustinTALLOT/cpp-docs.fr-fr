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
ms.openlocfilehash: 6a33f5b64c5094bfe2ca2ff259b5cd8654058ed3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502229"
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
|[CVSListBox:: GetItemText](#getitemtext)|Récupère le texte d’un élément de contrôle de liste modifiable. (Substitue `CVSListBoxBase::GetItemText`.)|
|[CVSListBox::GetSelItem](#getselitem)|Récupère l’index de base zéro de l’élément actuellement sélectionné dans un contrôle de liste modifiable. (Substitue `CVSListBoxBase::GetSelItem`.)|
|`CVSListBox::PreTranslateMessage`|Traduit les messages de fenêtre avant qu’ils ne soient distribués aux fonctions Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) et [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Pour plus d’informations et la syntaxe de méthode, consultez [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitue `CVSListBoxBase::PreTranslateMessage`.)|
|[CVSListBox::RemoveItem](#removeitem)|Supprime un élément d’un contrôle de liste modifiable. (Substitue `CVSListBoxBase::RemoveItem`.)|
|[CVSListBox::SelectItem](#selectitem)|Sélectionne une chaîne de contrôle de liste modifiable. (Substitue `CVSListBoxBase::SelectItem`.)|
|[CVSListBox::SetItemData](#setitemdata)|Associe une valeur 32 bits spécifique à l’application à un élément de contrôle de liste modifiable. (Substitue `CVSListBoxBase::SetItemData`.)|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|Retourne le handle du contrôle d’affichage de liste incorporé actuel.|

## <a name="remarks"></a>Notes

La `CVSListBox` classe fournit un ensemble de boutons modifier qui permettent à l’utilisateur de créer, de modifier, de supprimer ou de réorganiser les éléments d’un contrôle de liste.

Vous trouverez ci-dessous une image du contrôle de liste modifiable. La deuxième entrée de liste, intitulée «Item2», est sélectionnée pour modification.

![Contrôle CVSListBox](../../mfc/reference/media/cvslistbox.png "Contrôle CVSListBox")

Si vous utilisez l’éditeur de ressources pour ajouter un contrôle de liste modifiable, Notez que le volet **boîte à outils** de l’éditeur ne fournit pas de contrôle de liste modifiable prédéfini. Au lieu de cela, ajoutez un contrôle statique, tel que le contrôle **zone de groupe** . L’infrastructure utilise le contrôle statique comme espace réservé pour spécifier la taille et la position du contrôle de liste modifiable.

Pour utiliser un contrôle de liste modifiable dans un modèle de boîte de `CVSListBox` dialogue, déclarez une variable dans votre classe de boîte de dialogue. Pour prendre en charge l’échange de données entre la variable et le `DDX_Control` contrôle, définissez une `DoDataExchange` entrée de macro dans la méthode de la boîte de dialogue. Par défaut, le contrôle de liste modifiable est créé sans bouton modifier. Utilisez la méthode CVSListBoxBase:: SetStandardButtons héritée pour activer les boutons Modifier.

Pour plus d’informations, consultez le répertoire Samples `New Controls` , l’exemple, les fichiers page3. cpp et page3. h.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête:** afxvslistbox. h

##  <a name="additem"></a>  CVSListBox::AddItem

Ajoute une chaîne à un contrôle de liste.

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>Paramètres

*strIext*<br/>
dans Référence à une chaîne.

*dwData*<br/>
dans Valeur 32 bits spécifique à l’application qui est associée à la chaîne. La valeur par défaut est 0.

*iIndex*<br/>
dans Index de base zéro de la position qui contiendra la chaîne. Si le paramètre *iIndex* a la valeur-1, la chaîne est ajoutée à la fin de la liste. La valeur par défaut est -1.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la position de la chaîne dans le contrôle de liste.

### <a name="remarks"></a>Notes

Utilisez la méthode [CVSListBox:: GetItemData](#getitemdata) pour récupérer la valeur spécifiée par le paramètre *dwData* . Cette valeur peut être un entier spécifique à l’application ou un pointeur vers d’autres données.

##  <a name="cvslistbox"></a>  CVSListBox::CVSListBox

Construit un objet `CVSListBox`.

```
CVSListBox();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="edititem"></a>  CVSListBox::EditItem

Démarre une opération de modification sur le texte d’un élément de contrôle de liste.

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément de contrôle de liste.

### <a name="return-value"></a>Valeur de retour

TRUE si l’opération de modification commence avec succès; Sinon, FALSe.

### <a name="remarks"></a>Notes

L’utilisateur démarre une opération de modification en double-cliquant sur l’étiquette d’un élément, ou en appuyant sur la touche **F2** ou **barre d’espace** lorsqu’un élément a le focus.

##  <a name="getcount"></a>  CVSListBox::GetCount

Récupère le nombre de chaînes dans un contrôle de liste modifiable.

```
virtual int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d'éléments figurant dans le contrôle de liste.

### <a name="remarks"></a>Notes

Notez que le nombre est supérieur à la valeur d’index du dernier élément, car l’index est de base zéro.

##  <a name="getitemdata"></a>  CVSListBox::GetItemData

Récupère une valeur 32 bits spécifique à l’application qui est associée à un élément de contrôle de liste modifiable.

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément de contrôle de liste modifiable.

### <a name="return-value"></a>Valeur de retour

Valeur 32 bits associée à l’élément spécifié.

### <a name="remarks"></a>Notes

Utilisez la méthode [CVSListBox:: SetItemData](#setitemdata) ou [CVSListBox:: AddItem](#additem) pour associer la valeur 32 bits à l’élément de contrôle de liste. Cette valeur peut être un entier spécifique à l’application ou un pointeur vers d’autres données.

##  <a name="getitemtext"></a>  CVSListBox::GetItemText

Récupère le texte d’un élément de contrôle de liste modifiable.

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément de contrôle de liste modifiable.

### <a name="return-value"></a>Valeur de retour

Objet [CString](../../atl-mfc-shared/reference/cstringt-class.md) qui contient le texte de l’élément spécifié.

### <a name="remarks"></a>Notes

##  <a name="getlisthwnd"></a>  CVSListBox::GetListHwnd

Retourne le handle du contrôle d’affichage de liste incorporé actuel.

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>Valeur de retour

Handle du contrôle d’affichage de liste incorporé.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour récupérer un handle vers le contrôle d’affichage de liste incorporé `CVSListBox` qui prend en charge la classe.

##  <a name="getselitem"></a>  CVSListBox::GetSelItem

Récupère l’index de base zéro de l’élément actuellement sélectionné dans un contrôle de liste modifiable.

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>Valeur de retour

Si cette méthode est réussie, index de base zéro de l’élément actuellement sélectionné; Sinon,-1.

### <a name="remarks"></a>Notes

##  <a name="removeitem"></a>  CVSListBox::RemoveItem

Supprime un élément d’un contrôle de liste modifiable.

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément de contrôle de liste modifiable.

### <a name="return-value"></a>Valeur de retour

TRUE si l’élément spécifié est supprimé; Sinon, FALSe.

### <a name="remarks"></a>Notes

##  <a name="selectitem"></a>  CVSListBox::SelectItem

Sélectionne une chaîne de contrôle de liste modifiable.

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>Paramètres

*iItem*<br/>
dans Index de base zéro d’un élément de contrôle de liste modifiable.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit; Sinon, FALSe.

### <a name="remarks"></a>Notes

Cette méthode sélectionne l’élément spécifié et, si nécessaire, fait défiler l’élément dans l’affichage.

##  <a name="setitemdata"></a>  CVSListBox::SetItemData

Associe une valeur 32 bits spécifique à l’application à un élément de contrôle de liste modifiable.

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
dans Index de base zéro d’un élément de contrôle de liste modifiable.

*dwData*<br/>
dans Valeur 32 bits. Cette valeur peut être un entier spécifique à l’application ou un pointeur vers d’autres données.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
