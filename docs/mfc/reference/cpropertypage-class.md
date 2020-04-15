---
title: CPropertyPage, classe
ms.date: 11/04/2016
f1_keywords:
- CPropertyPage
- AFXDLGS/CPropertyPage
- AFXDLGS/CPropertyPage::CPropertyPage
- AFXDLGS/CPropertyPage::CancelToClose
- AFXDLGS/CPropertyPage::Construct
- AFXDLGS/CPropertyPage::GetPSP
- AFXDLGS/CPropertyPage::OnApply
- AFXDLGS/CPropertyPage::OnCancel
- AFXDLGS/CPropertyPage::OnKillActive
- AFXDLGS/CPropertyPage::OnOK
- AFXDLGS/CPropertyPage::OnQueryCancel
- AFXDLGS/CPropertyPage::OnReset
- AFXDLGS/CPropertyPage::OnSetActive
- AFXDLGS/CPropertyPage::OnWizardBack
- AFXDLGS/CPropertyPage::OnWizardFinish
- AFXDLGS/CPropertyPage::OnWizardNext
- AFXDLGS/CPropertyPage::QuerySiblings
- AFXDLGS/CPropertyPage::SetModified
- AFXDLGS/CPropertyPage::m_psp
helpviewer_keywords:
- CPropertyPage [MFC], CPropertyPage
- CPropertyPage [MFC], CancelToClose
- CPropertyPage [MFC], Construct
- CPropertyPage [MFC], GetPSP
- CPropertyPage [MFC], OnApply
- CPropertyPage [MFC], OnCancel
- CPropertyPage [MFC], OnKillActive
- CPropertyPage [MFC], OnOK
- CPropertyPage [MFC], OnQueryCancel
- CPropertyPage [MFC], OnReset
- CPropertyPage [MFC], OnSetActive
- CPropertyPage [MFC], OnWizardBack
- CPropertyPage [MFC], OnWizardFinish
- CPropertyPage [MFC], OnWizardNext
- CPropertyPage [MFC], QuerySiblings
- CPropertyPage [MFC], SetModified
- CPropertyPage [MFC], m_psp
ms.assetid: d9000a21-aa81-4530-85d9-f43432afb4dc
ms.openlocfilehash: 816948ea17f674c3cd693331502df33cce62610c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364002"
---
# <a name="cpropertypage-class"></a>CPropertyPage, classe

Représente des pages individuelles d'une feuille de propriétés, aussi connu sous le nom de boîte de dialogue d'onglet.

## <a name="syntax"></a>Syntaxe

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPropertyPage::CPropertyPage](#cpropertypage)|Construit un objet `CPropertyPage`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPropertyPage::CancelToClose](#canceltoclose)|Modifie le bouton OK pour lire Close, et désactive le bouton Annuler, après un changement irrécupérable dans la page d’une feuille de propriété modale.|
|[CPropertyPage::Construire](#construct)|Construit un objet `CPropertyPage`. Utilisez `Construct` si vous souhaitez spécifier vos paramètres au moment de l’exécution, ou si vous utilisez des tableaux.|
|[CPropertyPage::GetPSP](#getpsp)|Récupère la structure Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) associée à l’objet. `CPropertyPage`|
|[CPropertyPage::OnApply](#onapply)|Appelé par le cadre lorsque le bouton Apply Now est cliqué.|
|[CPropertyPage::OnCancel](#oncancel)|Appelé par le cadre lorsque le bouton Annuler est cliqué.|
|[CPropertyPage::OnKillActive](#onkillactive)|Appelé par le cadre lorsque la page actuelle n’est plus la page active. Effectuez la validation des données ici.|
|[CPropertyPage::OnOK](#onok)|Appelé par le cadre lorsque le bouton OK, Apply Now ou Close est cliqué.|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Appelé par le cadre lorsque le bouton Annuler est cliqué, et avant l’annulation a eu lieu.|
|[CPropertyPage::OnReset](#onreset)|Appelé par le cadre lorsque le bouton Annuler est cliqué.|
|[CPropertyPage::OnSetActive](#onsetactive)|Appelé par le cadre lorsque la page est faite la page active.|
|[CPropertyPage::OnWizardBack](#onwizardback)|Appelé par le cadre lorsque le bouton Back est cliqué à l’aide d’une feuille de propriété de type assistant.|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Appelé par le cadre lorsque le bouton Finition est cliqué à l’aide d’une feuille de propriété de type assistant.|
|[CPropertyPage::OnWizardNext](#onwizardnext)|Appelé par le cadre lorsque le bouton Suivant est cliqué à l’aide d’une feuille de propriété de type assistant.|
|[CPropertyPage::QuerySiblings](#querysiblings)|Transmette le message à chaque page de la feuille de propriété.|
|[CPropertyPage::SetModified](#setmodified)|Appelez pour activer ou désactiver le bouton Apply Now.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|La structure Windows [PROPSHEETPAGE.](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) Donne accès aux paramètres de base de la page de propriété.|

## <a name="remarks"></a>Notes

Comme avec les boîtes de dialogue `CPropertyPage` standard, vous dérivez une classe de chaque page dans votre feuille de propriété. Pour `CPropertyPage`utiliser des objets dérivés, créez d’abord un objet [CPropertySheet,](../../mfc/reference/cpropertysheet-class.md) puis créez un objet pour chaque page qui entre dans la feuille de propriété. Appelez [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) pour chaque page de la feuille, puis affichez la feuille de propriété en appelant [CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) pour une feuille de propriété modale, ou [CPropertySheet::Créer](../../mfc/reference/cpropertysheet-class.md#create) pour une feuille de propriété sans mode.

Vous pouvez créer un type de boîte de dialogue d’onglet appelé un assistant, qui se compose d’une feuille de propriété avec une séquence de pages de propriété qui guident l’utilisateur à travers les étapes d’une opération, comme la mise en place d’un appareil ou la création d’un bulletin. Dans une boîte de dialogue d’onglet de type sorcier, les pages de propriété n’ont pas d’onglets, et une seule page de propriété est visible à la fois. En outre, au lieu d’avoir OK et Appliquer maintenant boutons, une boîte de dialogue onglet de type assistant a un bouton arrière, un bouton Suivant ou Finition, et un bouton Annuler.

Pour plus d’informations sur l’établissement d’une feuille de propriété comme un assistant, voir [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Pour plus d’informations sur l’utilisation d’objets, `CPropertyPage` voir l’article Feuilles de propriété et pages de [propriété](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdlgs.h

## <a name="cpropertypagecanceltoclose"></a><a name="canceltoclose"></a>CPropertyPage::CancelToClose

Appelez cette fonction après qu’un changement irrécupérable a été apporté aux données dans une page d’une feuille de propriété modale.

```
void CancelToClose();
```

### <a name="remarks"></a>Notes

Cette fonction modifiera le bouton OK pour fermer et désactiver le bouton Annuler. Cette modification avertit l’utilisateur qu’un changement est permanent et que les modifications ne peuvent pas être annulées.

La `CancelToClose` fonction membre ne fait rien dans une feuille de propriété sans mode, parce qu’une feuille de propriété sans mode n’a pas de bouton Annuler par défaut.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertyPage:QuerySiblings](#querysiblings).

## <a name="cpropertypageconstruct"></a><a name="construct"></a>CPropertyPage::Construire

Appelez cette fonction de `CPropertyPage` membre pour construire un objet.

```
void Construct(
    UINT nIDTemplate,
    UINT nIDCaption = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0);

void Construct(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);

void Construct(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0);
```

### <a name="parameters"></a>Paramètres

*nIDTemplate (en)*<br/>
ID du modèle utilisé pour cette page.

*nIDCaption (en)*<br/>
ID du nom à placer dans l’onglet pour cette page. Si 0, le nom sera tiré du modèle de dialogue pour cette page.

*lpszTemplateName*<br/>
Contient une chaîne non terminée qui est le nom d’une ressource de modèle.

*nIDHeaderTitle (en)*<br/>
ID du nom à placer dans l’emplacement du titre de l’en-tête de la page de propriété. Par défaut, 0.

*nIDHeaderSubTitle*<br/>
ID du nom à placer dans l’emplacement sous-titre de l’en-tête de la page de propriété. Par défaut, 0.

### <a name="remarks"></a>Notes

L’objet est affiché après que toutes les conditions suivantes sont remplies :

- La page a été ajoutée à une feuille de propriété à l’aide [de CPropertySheet:AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- La fonction [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) or [Create](../../mfc/reference/cpropertysheet-class.md#create) de la feuille de propriété a été appelée.

- L’utilisateur a sélectionné (tabbed à) cette page.

Appelez `Construct` si l’un des autres constructeurs de classe n’a pas été appelé. La `Construct` fonction membre est flexible car vous pouvez laisser l’énoncé de paramètre vide, puis spécifier plusieurs paramètres et construction à tout moment de votre code.

Vous devez `Construct` utiliser lorsque vous travaillez avec `Construct` des tableaux, et vous devez appeler pour chaque membre du tableau afin que les membres de données soient attribués des valeurs appropriées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

## <a name="cpropertypagecpropertypage"></a><a name="cpropertypage"></a>CPropertyPage::CPropertyPage

Construit un objet `CPropertyPage`.

```
CPropertyPage();

explicit CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

explicit CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));

CPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption,
    UINT nIDHeaderTitle,
    UINT nIDHeaderSubTitle = 0,
    DWORD dwSize = sizeof(PROPSHEETPAGE));
```

### <a name="parameters"></a>Paramètres

*nIDTemplate (en)*<br/>
ID du modèle utilisé pour cette page.

*nIDCaption (en)*<br/>
ID du nom à placer dans l’onglet pour cette page. Si 0, le nom sera tiré du modèle de dialogue pour cette page.

*dwSize dwSize*<br/>
*lpszTemplateName* Points à une chaîne contenant le nom du modèle pour cette page. Ne peut pas avoir la valeur NULL.

*nIDHeaderTitle (en)*<br/>
ID du nom à placer dans l’emplacement du titre de l’en-tête de la page de propriété.

*nIDHeaderSubTitle*<br/>
ID du nom à placer dans l’emplacement sous-titre de l’en-tête de la page de propriété.

### <a name="remarks"></a>Notes

L’objet est affiché après que toutes les conditions suivantes sont remplies :

- La page a été ajoutée à une feuille de propriété à l’aide [de CPropertySheet:AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- La fonction [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) or [Create](../../mfc/reference/cpropertysheet-class.md#create) de la feuille de propriété a été appelée.

- L’utilisateur a sélectionné (tabbed à) cette page.

Si vous avez plusieurs paramètres (par exemple, si vous utilisez un tableau), utilisez `CPropertyPage` [CPropertySheet::Construire](../../mfc/reference/cpropertysheet-class.md#construct) au lieu de .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

## <a name="cpropertypagegetpsp"></a><a name="getpsp"></a>CPropertyPage::GetPSP

Récupère la structure Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) associée à l’objet. `CPropertyPage`

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Valeur de retour

Une référence `PROPSHEETPAGE` à la structure.

## <a name="cpropertypagem_psp"></a><a name="m_psp"></a>CPropertyPage::m_psp

`m_psp`est une structure dont les membres stockent les caractéristiques de [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2).

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Notes

Utilisez cette structure pour initialiser l’apparence d’une page de propriété après sa construction.

Pour plus d’informations sur cette structure, `PROPSHEETPAGE` y compris une liste de ses membres, voir dans le Windows SDK.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

## <a name="cpropertypageonapply"></a><a name="onapply"></a>CPropertyPage::OnApply

Cette fonction de membre est appelée par le cadre lorsque l’utilisateur choisit le bouton OK ou le bouton Apply Now.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les changements sont acceptés; sinon 0.

### <a name="remarks"></a>Notes

Lorsque le cadre appelle cette fonction, les modifications apportées sur toutes les pages `OnApply` de propriété de la feuille de propriété sont acceptées, la feuille de propriété conserve l’accent et renvoie TRUE (la valeur 1). Avant `OnApply` peut être appelé par le cadre, vous devez avoir appelé [SetModified](#setmodified) et définir son paramètre à VRAI. Cela activera le bouton Apply Now dès que l’utilisateur effectue une modification sur la page de propriété.

Remplacez cette fonction de membre pour spécifier l’action que prend votre programme lorsque l’utilisateur clique sur le bouton Apply Now. Lors de la suppression, la fonction doit retourner TRUE pour accepter les modifications et FALSE pour empêcher les changements d’entrer en vigueur.

La mise `OnApply` en `OnOK`œuvre par défaut des appels .

Pour plus d’informations sur les messages de notification envoyés lorsque l’utilisateur appuie sur le bouton Appliquer maintenant ou OK dans une feuille de propriété, voir [PSN_APPLY](/windows/win32/Controls/psn-apply) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertyPage:OnOK](#onok).

## <a name="cpropertypageoncancel"></a><a name="oncancel"></a>CPropertyPage::OnCancel

Cette fonction de membre est appelée par le cadre lorsque le bouton Annuler est sélectionné.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Notes

Remplacez cette fonction de membre pour effectuer des actions de bouton Annuler. La valeur par défaut annule toute modification qui a été apportée.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

## <a name="cpropertypageonkillactive"></a><a name="onkillactive"></a>CPropertyPage::OnKillActive

Cette fonction de membre est appelée par le cadre lorsque la page n’est plus la page active.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les données ont été mises à jour avec succès, sinon 0.

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre pour effectuer des tâches spéciales de validation des données.

La mise en œuvre par défaut de cette fonction membre copie les paramètres des contrôles de la page de propriété aux variables membres de la page de propriété. Si les données n’ont pas été mises à jour avec succès en raison d’une erreur de validation des données de dialogue (DDV), la page conserve la mise au point.

Une fois que cette fonction de membre sera re retour, le cadre appellera la fonction [OnOK](#onok) de la page.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

## <a name="cpropertypageonok"></a><a name="onok"></a>CPropertyPage::OnOK

Cette fonction membre est appelée par le cadre lorsque l’utilisateur choisit soit le bouton OK ou le bouton Apply Now, immédiatement après que le cadre appelle [OnKillActive](#onkillactive).

```
virtual void OnOK();
```

### <a name="remarks"></a>Notes

Lorsque l’utilisateur choisit le bouton OK ou le bouton Apply Now, le cadre reçoit la [notification PSN_APPLY](/windows/win32/Controls/psn-apply) de la page de propriété. L’appel `OnOK` à ne sera pas fait si vous appelez [CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) parce que la page de propriété n’envoie pas la notification dans ce cas.

Remplacer cette fonction de membre pour implémenter un comportement supplémentaire spécifique à la page actuellement active lorsque l’utilisateur rejette l’ensemble de la feuille de propriété.

La mise en œuvre par défaut de cette fonction membre indique `OnKillActive` que la page est « propre » pour tenir compte du fait que les données ont été mises à jour dans la fonction.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

## <a name="cpropertypageonquerycancel"></a><a name="onquerycancel"></a>CPropertyPage::OnQueryCancel

Cette fonction de membre est appelée par le cadre lorsque l’utilisateur clique sur le bouton Annuler et avant que l’action d’annulation n’ait eu lieu.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valeur de retour

Retourne FALSE pour empêcher l’opération d’annulation ou VRAI pour l’autoriser.

### <a name="remarks"></a>Notes

Remplacez cette fonction de membre pour spécifier une action que le programme prend lorsque l’utilisateur clique sur le bouton Annuler.

La mise `OnQueryCancel` en œuvre par défaut des retours TRUE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

## <a name="cpropertypageonreset"></a><a name="onreset"></a>CPropertyPage::OnReset

Cette fonction de membre est appelée par le cadre lorsque l’utilisateur choisit le bouton Annuler.

```
virtual void OnReset();
```

### <a name="remarks"></a>Notes

Lorsque le cadre appelle cette fonction, les modifications apportées à toutes les pages de propriété qui ont été faites par l’utilisateur qui choisissait précédemment le bouton Apply Now sont jetées, et la feuille de propriété conserve la mise au point.

Remplacez cette fonction de membre pour spécifier l’action que prend le programme lorsque l’utilisateur clique sur le bouton Annuler.

La mise `OnReset` en œuvre par défaut de ne fait rien.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertyPage:OnCancel](#oncancel).

## <a name="cpropertypageonsetactive"></a><a name="onsetactive"></a>CPropertyPage::OnSetActive

Cette fonction de membre est appelée par le cadre lorsque la page est choisie par l’utilisateur et devient la page active.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la page a été définie avec succès actif; sinon 0.

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre pour effectuer des tâches lorsqu’une page est activée. Votre remplacement de cette fonction de membre appelle généralement la version par défaut après la mise à jour des membres de données, pour lui permettre de mettre à jour les contrôles de page avec les nouvelles données.

L’implémentation par défaut crée la fenêtre de la page, si elle n’est pas créée précédemment, et en fait la page active.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CPropertySheet:SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

## <a name="cpropertypageonwizardback"></a><a name="onwizardback"></a>CPropertyPage::OnWizardBack

Cette fonction de membre est appelée par le cadre lorsque l’utilisateur clique sur le bouton Back dans un assistant.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Valeur de retour

0 pour passer automatiquement à la page suivante; -1 pour empêcher la page de changer. Pour sauter à une page autre que la suivante, retournez l’identifiant du dialogue à afficher.

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre pour spécifier certaines mesures que l’utilisateur doit prendre lorsque le bouton Back est appuyé.

Pour plus d’informations sur la façon de faire une feuille de propriété de type sorcier, voir [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

## <a name="cpropertypageonwizardfinish"></a><a name="onwizardfinish"></a>CPropertyPage::OnWizardFinish

Cette fonction de membre est appelée par le cadre lorsque l’utilisateur clique sur le bouton Finition dans un assistant.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la feuille de propriété est détruite lorsque l’assistant termine; autrement zéro.

### <a name="remarks"></a>Notes

Lorsqu’un utilisateur clique sur le bouton **Finition** dans un assistant, le cadre appelle cette fonction ; lorsque `OnWizardFinish` le rendement est VRAI (une valeur non zéro), la feuille de propriété peut être détruite (mais n’est pas réellement détruite). Appelez `DestroyWindow` pour détruire la feuille de propriété. N’appelez `DestroyWindow` `OnWizardFinish`pas de ; cela entraînera une corruption de tas ou d’autres erreurs.

Vous pouvez remplacer cette fonction de membre pour spécifier certaines mesures que l’utilisateur doit prendre lorsque le bouton Finition est appuyé. Lorsque vous dépassez cette fonction, retournez FALSE pour empêcher la feuille de propriété d’être détruite.

Pour plus d’informations sur les messages de notification envoyés lorsque l’utilisateur appuie sur le bouton Finition dans une feuille de propriété assistant, voir [PSN_WIZFINISH](/windows/win32/Controls/psn-wizfinish) dans le SDK Windows.

Pour plus d’informations sur la façon de faire une feuille de propriété de type sorcier, voir [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

## <a name="cpropertypageonwizardnext"></a><a name="onwizardnext"></a>CPropertyPage::OnWizardNext

Cette fonction de membre est appelée par le cadre lorsque l’utilisateur clique sur le bouton Suivant dans un assistant.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Valeur de retour

0 pour passer automatiquement à la page suivante; -1 pour empêcher la page de changer. Pour sauter à une page autre que la suivante, retournez l’identifiant du dialogue à afficher.

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre pour spécifier certaines mesures que l’utilisateur doit prendre lorsque le bouton Suivant est appuyé.

Pour plus d’informations sur la façon de faire une feuille de propriété de type sorcier, voir [CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

## <a name="cpropertypagequerysiblings"></a><a name="querysiblings"></a>CPropertyPage::QuerySiblings

Appelez cette fonction membre pour transmettre un message à chaque page de la feuille de propriété.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*wParam*<br/>
Spécifie des informations supplémentaires dépendantes des messages.

*lParam*<br/>
Spécifie des informations supplémentaires dépendantes des messages

### <a name="return-value"></a>Valeur de retour

La valeur non zéro d’une page dans la feuille de propriété, ou 0 si toutes les pages retournent une valeur de 0.

### <a name="remarks"></a>Notes

Si une page renvoie une valeur non zéro, la feuille de propriété n’envoie pas le message aux pages suivantes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

## <a name="cpropertypagesetmodified"></a><a name="setmodified"></a>CPropertyPage::SetModified

Appelez cette fonction membre pour activer ou désactiver le bouton Apply Now, en fonction de la question de savoir si les paramètres de la page de propriété doivent être appliqués à l’objet externe approprié.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Paramètres

*b Modifié*<br/>
VRAI pour indiquer que les paramètres de la page de propriété ont été modifiés depuis la dernière fois qu’ils ont été appliqués; FALSE pour indiquer que les paramètres de la page de propriété ont été appliqués, ou doivent être ignorés.

### <a name="remarks"></a>Notes

Le cadre garde une trace des pages qui sont «sales», `SetModified( TRUE )`c’est-à-dire, pages de propriété pour lesquelles vous avez appelé . Le bouton Apply Now sera toujours `SetModified( TRUE )` activé si vous appelez pour l’une des pages. Le bouton Apply Now sera `SetModified( FALSE )` désactivé lorsque vous appelez pour l’une des pages, mais seulement si aucune des autres pages n’est «sale».

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[MFC Échantillon PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet, classe](../../mfc/reference/cpropertysheet-class.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)
