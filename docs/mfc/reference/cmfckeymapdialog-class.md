---
description: 'En savoir plus sur : classe CMFCKeyMapDialog'
title: CMFCKeyMapDialog, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
ms.openlocfilehash: e339edb54b9c381dd2b27c9ee3ec7566308ae434
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265231"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog, classe

La `CMFCKeyMapDialog` classe prend en charge un contrôle qui mappe des commandes à des touches du clavier.

## <a name="syntax"></a>Syntaxe

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Construit un objet `CMFCKeyMapDialog`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCKeyMapDialog ::D oModal](#domodal)|Affiche une boîte de dialogue mappage du clavier.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Appelé par le Framework pour générer une chaîne qui décrit un mappage de clé. Par défaut, la chaîne contient le nom de la commande, les touches de raccourci utilisées et la description de la touche de raccourci.|
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Récupère une chaîne qui contient une liste de touches de raccourci associées à la commande spécifiée.|
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Appelé par le Framework avant qu’un nouvel élément soit inséré dans le contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.|
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Appelé par le Framework pour imprimer l’en-tête de la carte du clavier sur une nouvelle page.|
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Appelé par le Framework pour imprimer un élément de mappage du clavier.|
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Appelé par l’infrastructure pour définir des légendes pour les colonnes du contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.|
|[CMFCKeyMapDialog ::P rintKeyMap](#printkeymap)|Appelé par le Framework quand un utilisateur clique sur le bouton **Imprimer** .|
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Appelée par l’infrastructure pour définir la largeur des colonnes dans le contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.|

## <a name="remarks"></a>Notes

Utilisez la `CMFCKeyMapDialog` classe pour implémenter une boîte de dialogue de mappage du clavier redimensionnable. La boîte de dialogue utilise un contrôle d’affichage de liste pour afficher les raccourcis clavier et leurs commandes associées.

Pour utiliser la `CMFCKeyMapDialog` classe dans une application, transmettez un pointeur vers la fenêtre frame principale en tant que paramètre du `CMFCKeyMapDialog` constructeur. Appelez ensuite la `DoModal` méthode pour démarrer une boîte de dialogue modale.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxkeymapdialog. h

## <a name="cmfckeymapdialogcmfckeymapdialog"></a><a name="cmfckeymapdialog"></a> CMFCKeyMapDialog::CMFCKeyMapDialog

Construit un objet `CMFCKeyMapDialog`.

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>Paramètres

*pWndParentFrame*<br/>
dans Pointeur vers la fenêtre parente de l' `CMFCKeyMapDialog` objet.

*bEnablePrint*<br/>
dans TRUE si la liste des touches d’accès rapide peut être imprimée. Sinon, FALSe. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCKeyMapDialog` classe. Cet exemple fait partie de l' [exemple de démonstration Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

## <a name="cmfckeymapdialogdomodal"></a><a name="domodal"></a> CMFCKeyMapDialog ::D oModal

Affiche une boîte de dialogue mappage du clavier.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur renvoyée

Entier signé, tel que IDOK ou IDCANCEL, qui est passé à la méthode [CDialog :: EndDialog](../../mfc/reference/cdialog-class.md#enddialog) . La méthode ferme ensuite la boîte de dialogue. Pour plus d’informations, consultez [CDialog ::D omodal](../../mfc/reference/cdialog-class.md#domodal).

### <a name="remarks"></a>Notes

La boîte de dialogue mappage du clavier vous permet de sélectionner et d’affecter des touches accélérateur à différentes catégories de commandes. En outre, vous pouvez copier les touches accélérateur sélectionnées et leur description dans le presse-papiers.

## <a name="cmfckeymapdialogformatitem"></a><a name="formatitem"></a> CMFCKeyMapDialog::FormatItem

Appelé par le Framework pour générer une chaîne qui décrit un mappage de clé. Par défaut, la chaîne contient le nom de la commande, les touches de raccourci utilisées et la description de la touche de raccourci.

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>Paramètres

*nItem*<br/>
dans Index de base zéro d’un élément dans la liste interne des mappages de clés.

### <a name="return-value"></a>Valeur renvoyée

`CString`Objet qui contient le texte de l’élément mis en forme.

### <a name="remarks"></a>Notes

## <a name="cmfckeymapdialoggetcommandkeys"></a><a name="getcommandkeys"></a> CMFCKeyMapDialog::GetCommandKeys

Récupère une valeur de chaîne. La chaîne contient une liste de touches de raccourci associées à une commande spécifiée.

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>Paramètres

*uiCmdID*<br/>
dans ID de commande.

### <a name="return-value"></a>Valeur renvoyée

Liste délimitée par des points-virgules (« ; ») des touches de raccourci associées à la commande spécifiée.

### <a name="remarks"></a>Notes

## <a name="cmfckeymapdialogoninsertitem"></a><a name="oninsertitem"></a> CMFCKeyMapDialog::OnInsertItem

Appelée par l’infrastructure avant l’insertion d’un nouvel élément dans un contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
dans Pointeur vers un bouton de barre d’outils qui est utilisé pour mapper une combinaison de touches de clavier à un nom de commande et une description. L’élément de mappage de clés est stocké dans un contrôle de liste interne.

*nItem*<br/>
dans Index de base zéro qui spécifie où insérer le nouvel élément de mappage de clé dans le contrôle de liste interne.

### <a name="remarks"></a>Notes

## <a name="cmfckeymapdialogonprintheader"></a><a name="onprintheader"></a> CMFCKeyMapDialog::OnPrintHeader

Appelé par le Framework pour imprimer l’en-tête de la carte du clavier sur une nouvelle page.

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>Paramètres

*métafichier*<br/>
dans Contexte de périphérique pour l’imprimante.

*nPage*<br/>
dans Numéro de page à imprimer.

*adéquat*<br/>
dans Décalage horizontal de l’en-tête, en pixels.

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, hauteur du texte imprimé. Pour plus d’informations, consultez la section valeur de retour de [CDC ::D rawtext](../../mfc/reference/cdc-class.md#drawtext).

### <a name="remarks"></a>Notes

L’infrastructure utilise cette méthode pour imprimer la carte du clavier. Par défaut, cette méthode imprime le numéro de page, le nom de l’application et le titre de la boîte de dialogue.

## <a name="cmfckeymapdialogonprintitem"></a><a name="onprintitem"></a> CMFCKeyMapDialog::OnPrintItem

Appelé par le Framework pour imprimer un élément de mappage du clavier.

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>Paramètres

*métafichier*<br/>
dans Contexte de périphérique de l’imprimante.

*nItem*<br/>
dans Index de base zéro de l’élément à imprimer.

*y*<br/>
dans Décalage vertical entre le haut de la page et la position de l’élément.

*adéquat*<br/>
dans Décalage horizontal entre le côté gauche de la page et la position de l’élément.

*bCalcHeight*<br/>
dans TRUE pour calculer la hauteur optimale pour l’élément d’impression ; FALSe pour tronquer l’élément d’impression afin qu’il corresponde à l’espace par défaut.

### <a name="return-value"></a>Valeur renvoyée

Hauteur de l’élément imprimé.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode pour imprimer un élément de boîte de dialogue de mappage de clés. Par défaut, cette méthode imprime le nom de commande, les touches de raccourci et la description de commande de l’élément.

## <a name="cmfckeymapdialogonsetcolumns"></a><a name="onsetcolumns"></a> CMFCKeyMapDialog::OnSetColumns

Appelé par l’infrastructure pour définir des légendes pour les colonnes du contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode obtient les légendes des colonnes de trois ressources. La légende de la colonne de commande provient de IDS_AFXBARRES_COMMAND, la légende de la colonne clé provient de IDS_AFXBARRES_KEYS et la légende de la colonne Description est comprise entre IDS_AFXBARRES_DESCRIPTION.

## <a name="cmfckeymapdialogprintkeymap"></a><a name="printkeymap"></a> CMFCKeyMapDialog ::P rintKeyMap

Appelé par le Framework quand un utilisateur clique sur le bouton **Imprimer** .

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>Notes

La `PrintKeyMap` méthode imprime le mappage de clé. Il initie un nouveau travail d’impression, puis appelle à plusieurs reprises les méthodes [CMFCKeyMapDialog :: OnPrintHeader](#onprintheader) et [CMFCKeyMapDialog :: OnPrintItem](#onprintitem) jusqu’à ce que tous les mappages de touches soient imprimés.

## <a name="cmfckeymapdialogsetcolumnswidth"></a><a name="setcolumnswidth"></a> CMFCKeyMapDialog::SetColumnsWidth

Appelée par l’infrastructure pour définir la largeur des colonnes dans le contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>Notes

Cette méthode définit les colonnes du contrôle de liste interne sur les largeurs par défaut. Tout d’abord, la largeur de la colonne touches de raccourci est calculée. Ensuite, un tiers de la largeur restante est alloué à la colonne de commande et les deux tiers restants sont alloués à la colonne Description.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager, classe](../../mfc/reference/ckeyboardmanager-class.md)
