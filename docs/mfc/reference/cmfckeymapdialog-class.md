---
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
ms.openlocfilehash: 22aa006ce214ca720192bb761e2ff2b35a64fce3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374417"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog, classe

La `CMFCKeyMapDialog` classe prend en charge un contrôle qui cartographie les commandes aux touches du clavier.

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
|[CMFCKeyMapDialog::DoModal](#domodal)|Affiche une boîte de dialogue de cartographie du clavier.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Appelé par le cadre pour construire une chaîne qui décrit une cartographie clé. Par défaut, la chaîne contient le nom de commande, les touches de raccourci utilisées et la description des clés de raccourci.|
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Récupère une chaîne qui contient une liste de touches de raccourci associée à la commande spécifiée.|
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Appelé par le cadre avant qu’un nouvel élément soit inséré dans le contrôle de liste interne qui prend en charge le contrôle de cartographie du clavier.|
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Appelé par le cadre pour imprimer l’en-tête pour la carte du clavier sur une nouvelle page.|
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Appelé par le cadre pour imprimer un élément de cartographie du clavier.|
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Appelé par le cadre pour définir les légendes pour les colonnes dans le contrôle de liste interne qui prend en charge le contrôle de cartographie du clavier.|
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Appelé par le cadre lorsqu’un utilisateur clique sur le bouton **Imprimer.**|
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Appelé par le cadre pour définir la largeur des colonnes dans le contrôle de liste interne qui prend en charge le contrôle de cartographie du clavier.|

## <a name="remarks"></a>Notes

Utilisez `CMFCKeyMapDialog` la classe pour implémenter une boîte de dialogue de cartographie du clavier resizable. La boîte de dialogue utilise un contrôle de vue de liste pour afficher les raccourcis du clavier et leurs commandes associées.

Pour utiliser `CMFCKeyMapDialog` la classe dans une application, passez dans un pointeur `CMFCKeyMapDialog` à la fenêtre de cadre principale comme paramètre pour le constructeur. Ensuite, `DoModal` appelez la méthode pour démarrer une boîte de dialogue modal.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxkeymapdialog.h

## <a name="cmfckeymapdialogcmfckeymapdialog"></a><a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog

Construit un objet `CMFCKeyMapDialog`.

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>Paramètres

*pWndParentFrame*<br/>
[dans] Un pointeur à la `CMFCKeyMapDialog` fenêtre parente de l’objet.

*bEnablePrint*<br/>
[dans] VRAI si la liste des touches d’accélérateur peut être imprimée; autrement, FALSE. La valeur par défaut est FALSE.

### <a name="remarks"></a>Notes

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCKeyMapDialog` un objet de la classe. Cet exemple fait partie de [l’échantillon Visual Studio Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

## <a name="cmfckeymapdialogdomodal"></a><a name="domodal"></a>CMFCKeyMapDialog::DoModal

Affiche une boîte de dialogue de cartographie du clavier.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valeur de retour

Un intégriste signé, comme IDOK ou IDCANCEL, qui est transmis à la méthode [CDialog::EndDialog.](../../mfc/reference/cdialog-class.md#enddialog) La méthode, à son tour, ferme la boîte de dialogue. Pour plus d’informations, voir [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).

### <a name="remarks"></a>Notes

La boîte de dialogue de cartographie du clavier vous permet de sélectionner et d’attribuer des touches d’accélérateur à différentes catégories de commandes. En outre, vous pouvez copier les clés d’accélérateur sélectionnées et leur description au presse-papiers.

## <a name="cmfckeymapdialogformatitem"></a><a name="formatitem"></a>CMFCKeyMapDialog::FormatItem

Appelé par le cadre pour construire une chaîne qui décrit une cartographie clé. Par défaut, la chaîne contient le nom de commande, les touches de raccourci utilisées et la description des clés de raccourci.

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>Paramètres

*nItem (en)*<br/>
[dans] L’indice zéro d’un élément dans la liste interne des cartes clés.

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui contient le texte de l’élément formaté.

### <a name="remarks"></a>Notes

## <a name="cmfckeymapdialoggetcommandkeys"></a><a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys

Récupère une valeur de chaîne. La chaîne contient une liste de touches de raccourci qui sont associées à une commande spécifiée.

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>Paramètres

*uiCmdID*<br/>
[dans] Une pièce d’identité de commande.

### <a name="return-value"></a>Valeur de retour

Une liste de clés de raccourcis délimitées par le point de-œque (;) associée à la commande spécifiée.

### <a name="remarks"></a>Notes

## <a name="cmfckeymapdialogoninsertitem"></a><a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem

Appelé par le cadre avant qu’un nouvel élément soit inséré dans un contrôle de liste interne qui prend en charge le contrôle de cartographie du clavier.

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>Paramètres

*pButton*<br/>
[dans] Un pointeur vers un bouton de barre d’outils qui est utilisé pour cartographier une combinaison de touches de clavier à un nom de commande et une description. L’élément de la carte clé est stocké dans un contrôle de liste interne.

*nItem (en)*<br/>
[dans] Un index à base nulle qui précise où insérer le nouvel élément de la carte clé dans le contrôle de liste interne.

### <a name="remarks"></a>Notes

## <a name="cmfckeymapdialogonprintheader"></a><a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader

Appelé par le cadre pour imprimer l’en-tête pour la carte du clavier sur une nouvelle page.

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>Paramètres

*Dc*<br/>
[dans] Le contexte de l’appareil pour l’imprimante.

*nPage*<br/>
[dans] Le numéro de page à imprimer.

*Cx*<br/>
[dans] Le décalage horizontal de l’en-tête, en pixels.

### <a name="return-value"></a>Valeur de retour

En cas de succès, la hauteur du texte imprimé. Pour plus d’informations, consultez la section Valeur de retour de [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext).

### <a name="remarks"></a>Notes

Le cadre utilise cette méthode pour imprimer la carte du clavier. Par défaut, cette méthode imprime le numéro de page, le nom de l’application et le titre de boîte de dialogue.

## <a name="cmfckeymapdialogonprintitem"></a><a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem

Appelé par le cadre pour imprimer un élément de cartographie du clavier.

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>Paramètres

*Dc*<br/>
[dans] Le contexte de l’appareil de l’imprimante.

*nItem (en)*<br/>
[dans] L’index zéro de l’article à imprimer.

*y*<br/>
[dans] Le décalage vertical entre le haut de la page et la position de l’élément.

*Cx*<br/>
[dans] Le décalage horizontal entre la gauche de la page et la position de l’élément.

*bCalcHeight (en)*<br/>
[dans] VRAI pour calculer la meilleure hauteur pour l’article d’impression; FALSE pour tronquer l’élément d’impression afin qu’il s’adapte à l’espace par défaut.

### <a name="return-value"></a>Valeur de retour

La hauteur de l’article imprimé.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode pour imprimer un élément clé de boîte de dialogue de carte. Par défaut, cette méthode imprime le nom de commande de l’élément, les clés de raccourci et la description de commande.

## <a name="cmfckeymapdialogonsetcolumns"></a><a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns

Appelé par le cadre pour définir les légendes pour les colonnes dans le contrôle de liste interne qui prend en charge le contrôle de cartographie du clavier.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode obtient les légendes pour les colonnes à partir de trois ressources. La légende de colonne de commande provient de IDS_AFXBARRES_COMMAND, la légende de colonne clé provient de IDS_AFXBARRES_KEYS, et la légende de la colonne de description provient de IDS_AFXBARRES_DESCRIPTION.

## <a name="cmfckeymapdialogprintkeymap"></a><a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap

Appelé par le cadre lorsqu’un utilisateur clique sur le bouton **Imprimer.**

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>Notes

La `PrintKeyMap` méthode imprime la carte clé. Il initie un nouveau travail d’impression, puis appelle à plusieurs reprises le [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) et [CMFCKeyMapDialog::OnPrintItem](#onprintitem) méthodes jusqu’à ce que toutes les cartes clés sont imprimées.

## <a name="cmfckeymapdialogsetcolumnswidth"></a><a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth

Appelé par le cadre pour définir la largeur des colonnes dans le contrôle de liste interne qui prend en charge le contrôle de cartographie du clavier.

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>Notes

Cette méthode définit les colonnes du contrôle de liste interne aux largeurs par défaut. Tout d’abord, la largeur de la colonne des touches de raccourci est calculée. Ensuite, un tiers de la largeur restante est alloué à la colonne de commande et les deux tiers restants sont alloués à la colonne de description.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
