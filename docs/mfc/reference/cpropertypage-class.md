---
title: CPropertyPage (classe)
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
ms.openlocfilehash: 6a6223708c83f7a5b3e6532a2016660d558f8270
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421036"
---
# <a name="cpropertypage-class"></a>CPropertyPage (classe)

Représente des pages individuelles d'une feuille de propriétés, aussi connu sous le nom de boîte de dialogue d'onglet.

## <a name="syntax"></a>Syntaxe

```
class CPropertyPage : public CDialog
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CPropertyPage :: CPropertyPage](#cpropertypage)|Construit un objet `CPropertyPage`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CPropertyPage :: CancelToClose](#canceltoclose)|Modifie le bouton OK pour lire fermer et désactive le bouton Annuler, après une modification irrécupérable dans la page d’une feuille de propriétés modale.|
|[CPropertyPage :: Construct](#construct)|Construit un objet `CPropertyPage`. Utilisez `Construct` si vous souhaitez spécifier vos paramètres au moment de l’exécution, ou si vous utilisez des tableaux.|
|[CPropertyPage :: GetPSP](#getpsp)|Récupère la structure Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) associée à l’objet `CPropertyPage`.|
|[CPropertyPage :: OnApply](#onapply)|Appelé par l’infrastructure quand l’utilisateur clique sur le bouton appliquer.|
|[CPropertyPage :: OnCancel](#oncancel)|Appelé par le Framework lorsque l’utilisateur clique sur le bouton Annuler.|
|[CPropertyPage :: OnKillActive](#onkillactive)|Appelé par le Framework lorsque la page actuelle n’est plus la page active. Effectuez la validation des données ici.|
|[CPropertyPage :: OnOK](#onok)|Appelé par le Framework lorsque l’utilisateur clique sur le bouton OK, appliquer maintenant ou fermer.|
|[CPropertyPage :: OnQueryCancel](#onquerycancel)|Appelé par le Framework lorsque l’utilisateur clique sur le bouton Annuler et avant que l’annulation ait eu lieu.|
|[CPropertyPage :: OnReset](#onreset)|Appelé par le Framework lorsque l’utilisateur clique sur le bouton Annuler.|
|[CPropertyPage :: OnSetActive](#onsetactive)|Appelé par le Framework lorsque la page devient la page active.|
|[CPropertyPage :: OnWizardBack](#onwizardback)|Appelé par le Framework lorsque l’utilisateur clique sur le bouton précédent pendant l’utilisation d’une feuille de propriétés de type assistant.|
|[CPropertyPage :: OnWizardFinish](#onwizardfinish)|Appelé par le Framework lorsque l’utilisateur clique sur le bouton Terminer lors de l’utilisation d’une feuille de propriétés de type assistant.|
|[CPropertyPage :: OnWizardNext](#onwizardnext)|Appelé par le Framework lorsque l’utilisateur clique sur le bouton suivant pendant l’utilisation d’une feuille de propriétés de type assistant.|
|[CPropertyPage :: QuerySiblings](#querysiblings)|Transfère le message à chaque page de la feuille de propriétés.|
|[CPropertyPage :: SetModified](#setmodified)|Appelez pour activer ou désactiver le bouton Appliquer maintenant.|

### <a name="public-data-members"></a>Membres de données publics

|Name|Description|
|----------|-----------------|
|[CPropertyPage :: m_psp](#m_psp)|Structure [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) de Windows. Permet d’accéder aux paramètres de la page de propriétés de base.|

## <a name="remarks"></a>Notes

Comme pour les boîtes de dialogue standard, vous dérivez une classe de `CPropertyPage` pour chaque page de votre feuille de propriétés. Pour utiliser des objets dérivés de `CPropertyPage`, commencez par créer un objet [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) , puis créez un objet pour chaque page qui est insérée dans la feuille de propriétés. Appelez [CPropertySheet :: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) pour chaque page de la feuille, puis affichez la feuille de propriétés en appelant [CPropertySheet ::D omodal](../../mfc/reference/cpropertysheet-class.md#domodal) pour une feuille de propriétés modale, ou [CPropertySheet :: Create](../../mfc/reference/cpropertysheet-class.md#create) pour une feuille de propriétés non modale.

Vous pouvez créer un type de boîte de dialogue d’onglet appelé Assistant, qui se compose d’une feuille de propriétés avec une séquence de pages de propriétés qui guident l’utilisateur tout au long des étapes d’une opération, telles que la configuration d’un appareil ou la création d’un bulletin d’informations. Dans une boîte de dialogue d’onglets de type assistant, les pages de propriétés n’ont pas d’onglets et une seule page de propriétés est visible à la fois. En outre, au lieu d’avoir les boutons OK et appliquer maintenant, une boîte de dialogue d’onglet de type assistant contient un bouton précédent, un bouton suivant ou terminer, ainsi qu’un bouton Annuler.

Pour plus d’informations sur l’établissement d’une feuille de propriétés en tant qu’assistant, consultez [CPropertySheet :: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Pour plus d’informations sur l’utilisation d’objets `CPropertyPage`, consultez l’article [feuilles de propriétés et pages de propriétés](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdlgs. h

##  <a name="canceltoclose"></a>CPropertyPage :: CancelToClose

Appelez cette fonction après qu’une modification irrécupérable a été apportée aux données dans une page d’une feuille de propriétés modale.

```
void CancelToClose();
```

### <a name="remarks"></a>Notes

Cette fonction modifie le bouton OK pour fermer et désactiver le bouton Annuler. Cette modification avertit l’utilisateur qu’une modification est définitive et que les modifications ne peuvent pas être annulées.

La fonction membre `CancelToClose` n’a aucun effet dans une feuille de propriétés non modale, car une feuille de propriétés non modale n’a pas de bouton Annuler par défaut.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertyPage :: QuerySiblings](#querysiblings).

##  <a name="construct"></a>CPropertyPage :: Construct

Appelez cette fonction membre pour construire un objet `CPropertyPage`.

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

*nIDTemplate*<br/>
ID du modèle utilisé pour cette page.

*nIDCaption*<br/>
ID du nom à placer dans l’onglet de cette page. Si la valeur est 0, le nom est extrait du modèle de boîte de dialogue pour cette page.

*lpszTemplateName*<br/>
Contient une chaîne terminée par le caractère null qui est le nom d’une ressource de modèle.

*nIDHeaderTitle*<br/>
ID du nom à placer dans l’emplacement du titre de l’en-tête de la page de propriétés. Par défaut, 0.

*nIDHeaderSubTitle*<br/>
ID du nom à placer dans l’emplacement du sous-titre de l’en-tête de la page de propriétés. Par défaut, 0.

### <a name="remarks"></a>Notes

L’objet s’affiche une fois que toutes les conditions suivantes sont remplies :

- La page a été ajoutée à une feuille de propriétés à l’aide de [CPropertySheet :: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- La fonction [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) ou [Create](../../mfc/reference/cpropertysheet-class.md#create) de la feuille de propriétés a été appelée.

- L’utilisateur a sélectionné (avec des onglets) cette page.

Appelez `Construct` si l’un des autres constructeurs de classe n’a pas été appelé. La fonction membre `Construct` est flexible, car vous pouvez laisser l’instruction de paramètre vide, puis spécifier plusieurs paramètres et une construction à n’importe quel point de votre code.

Vous devez utiliser `Construct` lorsque vous travaillez avec des tableaux, et vous devez appeler `Construct` pour chaque membre du tableau afin que les valeurs appropriées soient affectées aux membres de données.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

##  <a name="cpropertypage"></a>CPropertyPage :: CPropertyPage

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

*nIDTemplate*<br/>
ID du modèle utilisé pour cette page.

*nIDCaption*<br/>
ID du nom à placer dans l’onglet de cette page. Si la valeur est 0, le nom est extrait du modèle de boîte de dialogue pour cette page.

*dwSize nul*<br/>
*lpszTemplateName* Pointe vers une chaîne contenant le nom du modèle pour cette page. Ne peut pas avoir la valeur NULL.

*nIDHeaderTitle*<br/>
ID du nom à placer dans l’emplacement du titre de l’en-tête de la page de propriétés.

*nIDHeaderSubTitle*<br/>
ID du nom à placer dans l’emplacement du sous-titre de l’en-tête de la page de propriétés.

### <a name="remarks"></a>Notes

L’objet s’affiche une fois que toutes les conditions suivantes sont remplies :

- La page a été ajoutée à une feuille de propriétés à l’aide de [CPropertySheet :: AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- La fonction [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) ou [Create](../../mfc/reference/cpropertysheet-class.md#create) de la feuille de propriétés a été appelée.

- L’utilisateur a sélectionné (avec des onglets) cette page.

Si vous avez plusieurs paramètres (par exemple, si vous utilisez un tableau), utilisez [CPropertySheet :: Construct](../../mfc/reference/cpropertysheet-class.md#construct) au lieu de `CPropertyPage`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

##  <a name="getpsp"></a>CPropertyPage :: GetPSP

Récupère la structure Windows [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2) associée à l’objet `CPropertyPage`.

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Valeur de retour

Référence à la structure `PROPSHEETPAGE`.

##  <a name="m_psp"></a>CPropertyPage :: m_psp

`m_psp` est une structure dont les membres stockent les caractéristiques de [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v2).

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Notes

Utilisez cette structure pour initialiser l’apparence d’une page de propriétés après qu’elle a été construite.

Pour plus d’informations sur cette structure, y compris la liste de ses membres, consultez `PROPSHEETPAGE` dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

##  <a name="onapply"></a>CPropertyPage :: OnApply

Cette fonction membre est appelée par l’infrastructure quand l’utilisateur choisit le bouton OK ou appliquer maintenant.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les modifications sont acceptées ; Sinon, 0.

### <a name="remarks"></a>Notes

Lorsque l’infrastructure appelle cette fonction, les modifications apportées à toutes les pages de propriétés de la feuille de propriétés sont acceptées, la feuille de propriétés conserve le focus et `OnApply` retourne TRUE (la valeur 1). Avant de pouvoir appeler `OnApply` par l’infrastructure, vous devez avoir appelé [SetModified](#setmodified) et définir son paramètre sur true. Cette opération active le bouton Appliquer maintenant dès que l’utilisateur apporte une modification dans la page de propriétés.

Substituez cette fonction membre pour spécifier l’action que votre programme prend lorsque l’utilisateur clique sur le bouton Appliquer maintenant. Lors de la substitution, la fonction doit retourner TRUE pour accepter les modifications et FALSe pour empêcher que les modifications prennent effet.

L’implémentation par défaut de `OnApply` appelle `OnOK`.

Pour plus d’informations sur les messages de notification envoyés lorsque l’utilisateur appuie sur le bouton Appliquer maintenant ou OK dans une feuille de propriétés, consultez [PSN_APPLY](/windows/win32/Controls/psn-apply) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertyPage :: OnOK](#onok).

##  <a name="oncancel"></a>CPropertyPage :: OnCancel

Cette fonction membre est appelée par le Framework lorsque le bouton Annuler est sélectionné.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Notes

Substituez cette fonction membre pour exécuter des actions de bouton Annuler. La valeur par défaut nie toutes les modifications apportées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

##  <a name="onkillactive"></a>CPropertyPage :: OnKillActive

Cette fonction membre est appelée par l’infrastructure lorsque la page n’est plus la page active.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les données ont été correctement mises à jour ; sinon, 0.

### <a name="remarks"></a>Notes

Substituez cette fonction membre pour effectuer des tâches de validation de données spéciales.

L’implémentation par défaut de cette fonction membre copie les paramètres des contrôles de la page de propriétés vers les variables membres de la page de propriétés. Si les données n’ont pas été correctement mises à jour en raison d’une erreur de validation des données de boîte de dialogue (DDV), la page conserve le focus.

Une fois que cette fonction membre a été retournée avec succès, l’infrastructure appellera la fonction [OnOK](#onok) de la page.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

##  <a name="onok"></a>CPropertyPage :: OnOK

Cette fonction membre est appelée par l’infrastructure quand l’utilisateur choisit le bouton OK ou appliquer maintenant, immédiatement après que le Framework a appelé [OnKillActive](#onkillactive).

```
virtual void OnOK();
```

### <a name="remarks"></a>Notes

Quand l’utilisateur choisit le bouton OK ou appliquer maintenant, le Framework reçoit la notification [PSN_APPLY](/windows/win32/Controls/psn-apply) à partir de la page de propriétés. L’appel à `OnOK` ne sera pas effectué si vous appelez [CPropertySheet ::P ressbutton](../../mfc/reference/cpropertysheet-class.md#pressbutton) , car la page de propriétés n’envoie pas la notification dans ce cas.

Substituez cette fonction membre pour implémenter un comportement supplémentaire spécifique à la page actuellement active lorsque l’utilisateur ignore la totalité de la feuille de propriétés.

L’implémentation par défaut de cette fonction membre marque la page comme « Clean » pour indiquer que les données ont été mises à jour dans la fonction `OnKillActive`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

##  <a name="onquerycancel"></a>CPropertyPage :: OnQueryCancel

Cette fonction membre est appelée par l’infrastructure quand l’utilisateur clique sur le bouton Annuler et avant que l’action d’annulation ait eu lieu.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valeur de retour

Retourne FALSe pour empêcher l’opération d’annulation ou TRUE pour l’autoriser.

### <a name="remarks"></a>Notes

Substituez cette fonction membre pour spécifier une action que le programme prend lorsque l’utilisateur clique sur le bouton Annuler.

L’implémentation par défaut de `OnQueryCancel` retourne la valeur TRUE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

##  <a name="onreset"></a>CPropertyPage :: OnReset

Cette fonction membre est appelée par l’infrastructure quand l’utilisateur choisit le bouton Annuler.

```
virtual void OnReset();
```

### <a name="remarks"></a>Notes

Lorsque l’infrastructure appelle cette fonction, les modifications apportées à toutes les pages de propriétés qui ont été effectuées par l’utilisateur qui ont précédemment choisi le bouton Appliquer maintenant sont ignorées, et la feuille de propriétés conserve le focus.

Substituez cette fonction membre pour spécifier l’action prise par le programme lorsque l’utilisateur clique sur le bouton Annuler.

L’implémentation par défaut de `OnReset` ne fait rien.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertyPage :: OnCancel](#oncancel).

##  <a name="onsetactive"></a>CPropertyPage :: OnSetActive

Cette fonction membre est appelée par l’infrastructure lorsque la page est choisie par l’utilisateur et devient la page active.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la page a été correctement définie ; Sinon, 0.

### <a name="remarks"></a>Notes

Substituez cette fonction membre pour effectuer des tâches lorsqu’une page est activée. La substitution de cette fonction membre appelle généralement la version par défaut après la mise à jour des membres de données, pour lui permettre de mettre à jour les contrôles de page avec les nouvelles données.

L’implémentation par défaut crée la fenêtre pour la page, si elle n’a pas été créée précédemment, et en fait la page active.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet :: SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

##  <a name="onwizardback"></a>CPropertyPage :: OnWizardBack

Cette fonction membre est appelée par l’infrastructure quand l’utilisateur clique sur le bouton précédent dans un Assistant.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Valeur de retour

0 pour avancer automatiquement jusqu’à la page suivante ; -1 pour empêcher la modification de la page. Pour accéder à une page autre que la suivante, renvoyez l’identificateur de la boîte de dialogue à afficher.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour spécifier une action que l’utilisateur doit effectuer quand l’utilisateur appuie sur le bouton précédent.

Pour plus d’informations sur la création d’une feuille de propriétés de type assistant, consultez [CPropertySheet :: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

##  <a name="onwizardfinish"></a>CPropertyPage :: OnWizardFinish

Cette fonction membre est appelée par l’infrastructure quand l’utilisateur clique sur le bouton Terminer dans un Assistant.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la feuille de propriétés est détruite à la fin de l’Assistant ; Sinon, zéro.

### <a name="remarks"></a>Notes

Quand un utilisateur clique sur le bouton **Terminer** dans un Assistant, l’infrastructure appelle cette fonction. Lorsque `OnWizardFinish` retourne TRUE (une valeur différente de zéro), la feuille de propriétés peut être détruite (mais n’est pas réellement détruite). Appelez `DestroyWindow` pour détruire la feuille de propriétés. N’appelez pas `DestroyWindow` à partir de `OnWizardFinish`; Cela entraînera une corruption du tas ou d’autres erreurs.

Vous pouvez remplacer cette fonction membre pour spécifier une action que l’utilisateur doit effectuer lorsque vous appuyez sur le bouton Terminer. Lors du remplacement de cette fonction, retournez FALSe pour empêcher la destruction de la feuille de propriétés.

Pour plus d’informations sur les messages de notification envoyés lorsque l’utilisateur appuie sur le bouton Terminer dans une feuille de propriétés de l’Assistant, consultez [PSN_WIZFINISH](/windows/win32/Controls/psn-wizfinish) dans le SDK Windows.

Pour plus d’informations sur la création d’une feuille de propriétés de type assistant, consultez [CPropertySheet :: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

##  <a name="onwizardnext"></a>CPropertyPage :: OnWizardNext

Cette fonction membre est appelée par l’infrastructure quand l’utilisateur clique sur le bouton suivant dans un Assistant.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Valeur de retour

0 pour avancer automatiquement jusqu’à la page suivante ; -1 pour empêcher la modification de la page. Pour accéder à une page autre que la suivante, renvoyez l’identificateur de la boîte de dialogue à afficher.

### <a name="remarks"></a>Notes

Substituez cette fonction membre pour spécifier une action que l’utilisateur doit effectuer lorsqu’il appuie sur le bouton suivant.

Pour plus d’informations sur la création d’une feuille de propriétés de type assistant, consultez [CPropertySheet :: SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

##  <a name="querysiblings"></a>CPropertyPage :: QuerySiblings

Appelez cette fonction membre pour transférer un message à chaque page de la feuille de propriétés.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*wParam*<br/>
Spécifie des informations supplémentaires dépendantes du message.

*lParam*<br/>
Spécifie des informations supplémentaires dépendantes du message

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro d’une page de la feuille de propriétés, ou 0 si toutes les pages retournent une valeur de 0.

### <a name="remarks"></a>Notes

Si une page retourne une valeur différente de zéro, la feuille de propriétés n’envoie pas le message aux pages suivantes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

##  <a name="setmodified"></a>CPropertyPage :: SetModified

Appelez cette fonction membre pour activer ou désactiver le bouton Appliquer maintenant, selon que les paramètres de la page de propriétés doivent être appliqués à l’objet externe approprié.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Paramètres

*bChanged*<br/>
TRUE pour indiquer que les paramètres de la page de propriétés ont été modifiés depuis la dernière application. FALSe pour indiquer que les paramètres de la page de propriétés ont été appliqués ou doivent être ignorés.

### <a name="remarks"></a>Notes

L’infrastructure effectue le suivi des pages qui sont « modifiées », c’est-à-dire des pages de propriétés pour lesquelles vous avez appelé `SetModified( TRUE )`. Le bouton Appliquer maintenant sera toujours activé si vous appelez `SetModified( TRUE )` pour l’une des pages. Le bouton Appliquer maintenant est désactivé lorsque vous appelez `SetModified( FALSE )` pour l’une des pages, mais uniquement si aucune autre page n’est « modifiée ».

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet, classe](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)
