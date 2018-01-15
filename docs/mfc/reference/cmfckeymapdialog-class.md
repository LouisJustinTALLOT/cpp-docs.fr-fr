---
title: Classe de CMFCKeyMapDialog | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1965e5dd2d522175b3709449df9a0b8575e20c59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cmfckeymapdialog-class"></a>Classe de CMFCKeyMapDialog
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
|[CMFCKeyMapDialog::DoModal](#domodal)|Affiche une boîte de dialogue de mappage de clavier.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Appelé par le framework pour générer une chaîne qui décrit un mappage de clé. Par défaut, la chaîne contient le nom de commande, les touches de raccourci utilisées et la description de la clé contextuel.|  
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Récupère une chaîne qui contient une liste des touches de raccourci associée à la commande spécifiée.|  
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Appelé par l’infrastructure avant un nouvel élément est inséré dans le contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.|  
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Appelé par l’infrastructure pour imprimer l’en-tête pour le mappage du clavier sur une nouvelle page.|  
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Appelé par l’infrastructure pour imprimer un élément de mappage du clavier.|  
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Appelé par l’infrastructure pour définir des légendes pour les colonnes dans le contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.|  
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Appelé par l’infrastructure lorsqu’un utilisateur clique sur le **impression** bouton.|  
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Appelé par l’infrastructure pour définir la largeur des colonnes dans le contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.|  
  
## <a name="remarks"></a>Notes  
 Utilisez la `CMFCKeyMapDialog` classe pour implémenter une boîte de dialogue de mappage de clavier redimensionnable. La boîte de dialogue utilise un contrôle list view pour afficher les raccourcis clavier et leurs commandes associées.  
  
 Pour utiliser le `CMFCKeyMapDialog` classe dans une application, passez un pointeur vers la fenêtre frame principale en tant que paramètre à la `CMFCKeyMapDialog` constructeur. Appelez ensuite la `DoModal` méthode pour démarrer une boîte de dialogue modale.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxkeymapdialog.h  
  
##  <a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog  
 Construit un objet `CMFCKeyMapDialog`.  
  
```  
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bEnablePrint=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndParentFrame`  
 Un pointeur vers la fenêtre parente de la `CMFCKeyMapDialog` objet.  
  
 [in] `bEnablePrint`  
 `TRUE`Si la liste des touches d’accès peut être imprimée ; dans le cas contraire, `FALSE`. La valeur par défaut est `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCKeyMapDialog` classe. Cet exemple fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]  
  
##  <a name="domodal"></a>CMFCKeyMapDialog::DoModal  
 Affiche une boîte de dialogue de mappage de clavier.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un entier signé, tel que `IDOK` ou `IDCANCEL`, qui est passé à la [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog) (méthode). La méthode, ferme à son tour, la boîte de dialogue. Pour plus d’informations, consultez [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).  
  
### <a name="remarks"></a>Notes  
 La boîte de dialogue de mappage de clavier permet de sélectionner et assigner des touches accélérateur pour différentes catégories de commandes. En outre, vous pouvez copier les touches accélérateur sélectionné et leur description dans le Presse-papiers.  
  
##  <a name="formatitem"></a>CMFCKeyMapDialog::FormatItem  
 Appelé par le framework pour générer une chaîne qui décrit un mappage de clé. Par défaut, la chaîne contient le nom de commande, les touches de raccourci utilisées et la description de la clé contextuel.  
  
```  
virtual CString FormatItem(int nItem) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nItem`  
 Index de base zéro d’un élément dans la liste interne des mappages de touches.  
  
### <a name="return-value"></a>Valeur de retour  
 A `CString` objet qui contient le texte de l’élément mis en forme.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys  
 Récupère une valeur de chaîne. La chaîne contient une liste des touches de raccourci qui sont associées à une commande spécifiée.  
  
```  
virtual CString GetCommandKeys(UINT uiCmdID) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `uiCmdID`  
 Un ID de commande.  
  
### <a name="return-value"></a>Valeur de retour  
 Un point-virgule (« ; ») liste des touches de raccourci associée à la commande spécifiée.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem  
 Appelé par l’infrastructure avant un nouvel élément est inséré dans un contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.  
  
```  
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,  
    int nItem);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pButton`  
 Pointeur vers un bouton de barre d’outils qui est utilisé pour mapper une combinaison de touches du clavier pour un nom de commande et une description. L’élément de mappage de clés est stockée dans un contrôle de liste interne.  
  
 [in] `nItem`  
 Index de base zéro qui spécifie l’emplacement où insérer le nouvel élément de mappage de clés dans le contrôle de liste interne.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader  
 Appelé par l’infrastructure pour imprimer l’en-tête pour le mappage du clavier sur une nouvelle page.  
  
```  
virtual int OnPrintHeader(
    CDC& dc,  
    int nPage,  
    int cx) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dc`  
 Le contexte de périphérique pour l’imprimante.  
  
 [in] `nPage`  
 Le numéro de page à imprimer.  
  
 [in] `cx`  
 Le décalage horizontal de l’en-tête, en pixels.  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, la hauteur du texte imprimé. Pour plus d’informations, consultez la section de la valeur de retour de [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext).  
  
### <a name="remarks"></a>Notes  
 L’infrastructure utilise cette méthode pour imprimer le mappage du clavier. Par défaut, cette méthode affiche le numéro de page, le nom de l’application et le titre de la boîte de dialogue.  
  
##  <a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem  
 Appelé par l’infrastructure pour imprimer un élément de mappage du clavier.  
  
```  
virtual int OnPrintItem(
    CDC& dc,  
    int nItem,  
    int y,  
    int cx,  
    BOOL bCalcHeight) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dc`  
 Le contexte de périphérique de l’imprimante.  
  
 [in] `nItem`  
 Index de base zéro de l’élément à imprimer.  
  
 [in] `y`  
 Le décalage vertical entre le haut de la page et la position de l’élément.  
  
 [in] `cx`  
 Le décalage horizontal entre la gauche de la page et la position de l’élément.  
  
 [in] `bCalcHeight`  
 `TRUE`pour calculer la hauteur meilleures pour l’élément d’impression ; `FALSE` tronquer l’élément impression afin qu’elle s’adapte à l’espace par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 La hauteur de l’élément.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode pour imprimer un élément de boîte de dialogue mappage de clés. Par défaut, cette méthode affiche le nom de la commande de l’élément, les touches de raccourci et description de la commande.  
  
##  <a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns  
 Appelé par l’infrastructure pour définir des légendes pour les colonnes dans le contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.  
  
```  
virtual void OnSetColumns();
```  
  
### <a name="remarks"></a>Notes  
 Par défaut, cette méthode obtient les légendes pour les colonnes à partir de trois ressources. La légende de la colonne commande à partir de IDS_AFXBARRES_COMMAND, la légende de la colonne clé est de IDS_AFXBARRES_KEYS, et la légende de la colonne description à partir IDS_AFXBARRES_DESCRIPTION.  
  
##  <a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap  
 Appelé par l’infrastructure lorsqu’un utilisateur clique sur le **impression** bouton.  
  
```  
virtual void PrintKeyMap();
```  
  
### <a name="remarks"></a>Notes  
 Le `PrintKeyMap` méthode imprime le mappage de clés. Il lance un nouveau travail d’impression et appelle à plusieurs reprises la [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) et [CMFCKeyMapDialog::OnPrintItem](#onprintitem) méthodes jusqu'à ce que tous les mappages de clé sont imprimés.  
  
##  <a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth  
 Appelé par l’infrastructure pour définir la largeur des colonnes dans le contrôle de liste interne qui prend en charge le contrôle de mappage du clavier.  
  
```  
virtual void SetColumnsWidth();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode définit les colonnes du contrôle de la liste interne de largeur de la valeur par défaut. Tout d’abord, la largeur de la colonne de touches de raccourci est calculée. Un tiers de la largeur restante est alloué à la colonne de la commande, puis les deux tiers restants est allouée à la colonne description.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager, classe](../../mfc/reference/ckeyboardmanager-class.md)
