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
ms.openlocfilehash: 1816e6ee2dc0f358cb2da4c8bab572daa33a29c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561237"
---
# <a name="cpropertypage-class"></a>CPropertyPage (classe)

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
|[CPropertyPage::CancelToClose](#canceltoclose)|Modifie le bouton OK pour fermer de lire et désactive le bouton Annuler, après une modification non récupérable dans la page d’une feuille de propriétés modale.|
|[CPropertyPage::Construct](#construct)|Construit un objet `CPropertyPage`. Utilisez `Construct` si vous souhaitez spécifier vos paramètres en cours d’exécution, ou si vous utilisez des tableaux.|
|[CPropertyPage::GetPSP](#getpsp)|Récupère le Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) structure associée à la `CPropertyPage` objet.|
|[CPropertyPage::OnApply](#onapply)|Appelé par le framework lorsque l’utilisateur clique sur le bouton Appliquer.|
|[CPropertyPage::OnCancel](#oncancel)|Appelé par le framework lorsque l’utilisateur clique sur le bouton Annuler.|
|[CPropertyPage::OnKillActive](#onkillactive)|Appelé par le framework lorsque la page actuelle n’est plus la page active. Effectuer la validation de données ici.|
|[CPropertyPage::OnOK](#onok)|Appelé par le framework lorsque le OK, appliquer ou bouton Fermer est activé.|
|[CPropertyPage::OnQueryCancel](#onquerycancel)|Appelé par le framework lorsque l’utilisateur clique sur le bouton Annuler, et avant l’annulation a eu lieu.|
|[CPropertyPage::OnReset](#onreset)|Appelé par le framework lorsque l’utilisateur clique sur le bouton Annuler.|
|[Notifications CPropertyPage::OnSetActive](#onsetactive)|Appelé par l’infrastructure lors de la page devient la page active.|
|[CPropertyPage::OnWizardBack](#onwizardback)|Appelé par le framework lorsque l’utilisateur clique sur le bouton précédent lors de l’utilisation d’une feuille de propriétés de type de l’Assistant.|
|[CPropertyPage::OnWizardFinish](#onwizardfinish)|Appelé par le framework lorsque l’utilisateur clique sur le bouton Terminer lors de l’utilisation d’une feuille de propriétés de type de l’Assistant.|
|[CPropertyPage::OnWizardNext](#onwizardnext)|Appelé par le framework lorsque l’utilisateur clique sur le bouton suivant lors de l’utilisation d’une feuille de propriétés de type de l’Assistant.|
|[CPropertyPage::QuerySiblings](#querysiblings)|Transfère le message à chaque page de la feuille de propriétés.|
|[CPropertyPage::SetModified](#setmodified)|L’appel pour activer ou désactiver le bouton Appliquer.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPropertyPage::m_psp](#m_psp)|Le Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) structure. Fournit l’accès aux paramètres de page de propriété de base.|

## <a name="remarks"></a>Notes

Comme avec les boîtes de dialogue standard, vous dérivez une classe de `CPropertyPage` pour chaque page dans votre feuille de propriétés. Pour utiliser `CPropertyPage`-objets dérivés, commencez par créer un [CPropertySheet](../../mfc/reference/cpropertysheet-class.md) de l’objet, puis créer un objet pour chaque page qui s’intègre dans la feuille de propriétés. Appelez [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage) pour chaque page dans la feuille et afficher la feuille de propriétés en appelant [CPropertySheet::DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) pour une feuille de propriétés modale ou [CPropertySheet :: Créer](../../mfc/reference/cpropertysheet-class.md#create) pour une feuille de propriétés non modale.

Vous pouvez créer un type de boîte de dialogue d’onglet appelé Assistant, ce qui se compose d’une feuille de propriétés avec une séquence de pages de propriétés qui guident les utilisateurs à travers les étapes d’une opération, telles que la configuration d’un appareil ou un bulletin d’informations. Dans une boîte de dialogue type d’Assistant onglet, les pages de propriétés n’ont pas de tabulations, et uniquement une page de propriété est visible à la fois. En outre, au lieu de boutons OK et appliquer maintenant, une boîte de dialogue type d’Assistant onglet a un bouton précédent, un bouton suivant ou terminer et un bouton Annuler.

Pour plus d’informations sur l’établissement d’une feuille de propriétés en tant qu’un Assistant, consultez [fonction CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode). Pour plus d’informations sur l’utilisation de `CPropertyPage` objets, consultez l’article [feuilles de propriétés et Pages de propriétés](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CPropertyPage`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdlgs.h

##  <a name="canceltoclose"></a>  CPropertyPage::CancelToClose

Appelez cette fonction après qu’une modification irrécupérable a été apportée aux données dans une page d’une feuille de propriétés modale.

```
void CancelToClose();
```

### <a name="remarks"></a>Notes

Cette fonction modifie le bouton OK pour fermer et désactive le bouton Annuler. Modifier les alertes de l’utilisateur qu’une modification est définitive et les modifications ne peut pas être annulée.

Le `CancelToClose` fonction membre ne fait rien dans une feuille de propriétés non modale, car une feuille de propriétés non modale ne dispose pas d’un bouton Annuler par défaut.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertyPage::QuerySiblings](#querysiblings).

##  <a name="construct"></a>  CPropertyPage::Construct

Appelez cette fonction membre pour construire un `CPropertyPage` objet.

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
ID du nom est placé dans l’onglet de cette page. Si 0, le nom s’affichera dans le modèle de boîte de dialogue pour cette page.

*lpszTemplateName*<br/>
Contient une chaîne se terminant par null qui est le nom d’une ressource de modèle.

*nIDHeaderTitle*<br/>
ID du nom est placé dans l’emplacement de titre de l’en-tête de page de propriété. Par défaut, 0.

*nIDHeaderSubTitle*<br/>
ID du nom est placé dans l’emplacement de sous-titre de l’en-tête de page de propriété. Par défaut, 0.

### <a name="remarks"></a>Notes

L’objet s’affiche une fois que toutes les conditions suivantes sont remplies :

- La page a été ajoutée à une feuille de propriété à l’aide [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- La feuille de propriétés [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) ou [créer](../../mfc/reference/cpropertysheet-class.md#create) fonction a été appelée.

- L’utilisateur a sélectionné (tabulé) cette page.

Appeler `Construct` si un des autres constructeurs de classe n’a pas été appelé. Le `Construct` la fonction membre est flexible car vous pouvez laisser l’instruction de paramètre vide, puis spécifiez plusieurs paramètres et la construction à tout moment dans votre code.

Vous devez utiliser `Construct` lorsque vous travaillez avec des tableaux, et vous devez appeler `Construct` pour chaque membre du tableau d’afin que les membres de données sont affectées des valeurs appropriées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#112](../../mfc/codesnippet/cpp/cpropertypage-class_1.cpp)]

##  <a name="cpropertypage"></a>  CPropertyPage::CPropertyPage

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
ID du nom est placé dans l’onglet de cette page. Si 0, le nom s’affichera dans le modèle de boîte de dialogue pour cette page.

*dwSize*<br/>
*lpszTemplateName* pointe vers une chaîne contenant le nom du modèle pour cette page. Ne peut pas être Null.

*nIDHeaderTitle*<br/>
ID du nom est placé dans l’emplacement de titre de l’en-tête de page de propriété.

*nIDHeaderSubTitle*<br/>
ID du nom est placé dans l’emplacement de sous-titre de l’en-tête de page de propriété.

### <a name="remarks"></a>Notes

L’objet s’affiche une fois que toutes les conditions suivantes sont remplies :

- La page a été ajoutée à une feuille de propriété à l’aide [CPropertySheet::AddPage](../../mfc/reference/cpropertysheet-class.md#addpage).

- La feuille de propriétés [DoModal](../../mfc/reference/cpropertysheet-class.md#domodal) ou [créer](../../mfc/reference/cpropertysheet-class.md#create) fonction a été appelée.

- L’utilisateur a sélectionné (tabulé) cette page.

Si vous avez plusieurs paramètres (par exemple, si vous utilisez un tableau), utilisez [CPropertySheet::Construct](../../mfc/reference/cpropertysheet-class.md#construct) au lieu de `CPropertyPage`.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#113](../../mfc/codesnippet/cpp/cpropertypage-class_2.cpp)]

##  <a name="getpsp"></a>  CPropertyPage::GetPSP

Récupère le Windows [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2) structure associée à la `CPropertyPage` objet.

```
const PROPSHEETPAGE& GetPSP() const;

PROPSHEETPAGE& GetPSP();
```

### <a name="return-value"></a>Valeur de retour

Une référence à la `PROPSHEETPAGE` structure.

##  <a name="m_psp"></a>  CPropertyPage::m_psp

`m_psp` est une structure dont les membres stockent les caractéristiques de [PROPSHEETPAGE](/windows/desktop/api/prsht/ns-prsht-_propsheetpagea_v2).

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Notes

Utilisez cette structure pour initialiser l’apparence d’une page de propriétés après sa construction.

Pour plus d’informations sur cette structure, y compris une liste de ses membres, consultez `PROPSHEETPAGE` dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#128](../../mfc/codesnippet/cpp/cpropertypage-class_3.cpp)]

##  <a name="onapply"></a>  CPropertyPage::OnApply

Cette fonction membre est appelée par le framework lorsque l’utilisateur choisit le OK ou le bouton Appliquer.

```
virtual BOOL OnApply();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les modifications sont acceptées ; sinon 0.

### <a name="remarks"></a>Notes

Lorsque l’infrastructure appelle cette fonction, les modifications effectuées sur toutes les pages de propriétés dans la feuille de propriétés sont acceptées, la feuille de propriétés conserve le focus, et `OnApply` retourne la valeur TRUE (la valeur 1). Avant de `OnApply` peut être appelée par l’infrastructure, vous devez appeler [SetModified](#setmodified) et son paramètre la valeur TRUE. Cela active le bouton Appliquer dès que l’utilisateur apporte une modification sur la page de propriétés.

Remplacez cette fonction membre pour spécifier l’action prise par votre programme lorsque l’utilisateur clique sur le bouton Appliquer. Lors de la substitution, la fonction doit retourner TRUE pour accepter les modifications et FALSE pour empêcher les modifications de prendre effet.

L’implémentation par défaut de `OnApply` appels `OnOK`.

Pour plus d’informations sur les messages de notification envoyés lorsque l’utilisateur appuie sur les appliquer maintenant ou bouton OK dans une feuille de propriétés, consultez [PSN_APPLY](/windows/desktop/Controls/psn-apply) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertyPage::OnOK](#onok).

##  <a name="oncancel"></a>  CPropertyPage::OnCancel

Cette fonction membre est appelée par le framework lorsque le bouton Annuler est sélectionné.

```
virtual void OnCancel();
```

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour effectuer des actions de bouton Annuler. La valeur par défaut inverse toutes les modifications qui ont été apportées.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#114](../../mfc/codesnippet/cpp/cpropertypage-class_4.cpp)]

##  <a name="onkillactive"></a>  CPropertyPage::OnKillActive

Cette fonction membre est appelée par le framework lorsque la page n’est plus la page active.

```
virtual BOOL OnKillActive();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les données a été mis à jour avec succès, sinon 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour effectuer des tâches de validation de données spéciaux.

L’implémentation par défaut de cette fonction membre copie les paramètres des contrôles dans la page de propriétés pour les variables de membre de la page de propriétés. Si les données n’a été pas été correctement mis à jour en raison d’une erreur de validation (DDV) de données de boîte de dialogue, la page conserve le focus.

Une fois que cette fonction membre est retournée avec succès, l’infrastructure appellera la page [OnOK](#onok) (fonction).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#115](../../mfc/codesnippet/cpp/cpropertypage-class_5.cpp)]

##  <a name="onok"></a>  CPropertyPage::OnOK

Cette fonction membre est appelée par l’infrastructure quand l’utilisateur choisit le OK ou sur le bouton Appliquer, immédiatement après le framework appelle [OnKillActive](#onkillactive).

```
virtual void OnOK();
```

### <a name="remarks"></a>Notes

Lorsque l’utilisateur choisit le OK ou sur le bouton Appliquer, l’infrastructure reçoit le [PSN_APPLY](/windows/desktop/Controls/psn-apply) notification à partir de la page de propriétés. L’appel à `OnOK` ne sont pas être effectuées si vous appelez [CPropertySheet::PressButton](../../mfc/reference/cpropertysheet-class.md#pressbutton) , car la page de propriétés n’envoie pas la notification dans ce cas.

Remplacez cette fonction membre pour implémenter un comportement supplémentaire spécifique à la page actuellement active lorsque l’utilisateur ferme la feuille de propriétés entière.

L’implémentation par défaut de cette fonction membre marque la page en tant que « nettoyer » pour refléter que les données a été mis à jour dans le `OnKillActive` (fonction).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#116](../../mfc/codesnippet/cpp/cpropertypage-class_6.cpp)]

##  <a name="onquerycancel"></a>  CPropertyPage::OnQueryCancel

Cette fonction membre est appelée par le framework lorsque l’utilisateur clique sur le bouton Annuler et avant l’annulation action a eu lieu.

```
virtual BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur FALSE pour empêcher l’opération d’annulation ou TRUE pour lui permettre de.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour spécifier une action que le programme prend lorsque l’utilisateur clique sur le bouton Annuler.

L’implémentation par défaut de `OnQueryCancel` retourne la valeur TRUE.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#117](../../mfc/codesnippet/cpp/cpropertypage-class_7.cpp)]

##  <a name="onreset"></a>  CPropertyPage::OnReset

Cette fonction membre est appelée par le framework lorsque l’utilisateur choisit le bouton Annuler.

```
virtual void OnReset();
```

### <a name="remarks"></a>Notes

Lorsque l’infrastructure appelle cette fonction, toutes les pages de propriétés qui ont été apportées par l’utilisateur précédemment en choisissant le bouton Appliquer les modifications sont ignorées, et la feuille de propriétés conserve le focus.

Remplacez cette fonction membre pour spécifier l’action que le programme prend lorsque l’utilisateur clique sur le bouton Annuler.

L’implémentation par défaut de `OnReset` ne fait rien.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertyPage::OnCancel](#oncancel).

##  <a name="onsetactive"></a>  Notifications CPropertyPage::OnSetActive

Cette fonction membre est appelée par le framework lorsque la page est choisie par l’utilisateur et devient la page active.

```
virtual BOOL OnSetActive();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la page a été définie correctement active ; sinon 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour effectuer des tâches lorsqu’une page est activée. La substitution de cette fonction membre appelez généralement la version par défaut après la mise à jour des membres de données, pour lui permettre de mettre à jour les contrôles de page avec les nouvelles données.

L’implémentation par défaut crée la fenêtre de la page, si ce n’est pas créé précédemment et rend la page active.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CPropertySheet::SetFinishText](../../mfc/reference/cpropertysheet-class.md#setfinishtext).

##  <a name="onwizardback"></a>  CPropertyPage::OnWizardBack

Cette fonction membre est appelée par le framework lorsque l’utilisateur clique sur le bouton précédent dans un Assistant.

```
virtual LRESULT OnWizardBack();
```

### <a name="return-value"></a>Valeur de retour

0 pour passer automatiquement à la page suivante ; -1 pour empêcher la modification de la page. Pour accéder à une page différente de celle qui suit, retourner l’identificateur de la boîte de dialogue à afficher.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour spécifier une action de que l’utilisateur doit effectuer lorsque vous appuyez sur le bouton précédent.

Pour plus d’informations sur la façon de rendre une feuille de propriétés de type de l’Assistant, consultez [fonction CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#118](../../mfc/codesnippet/cpp/cpropertypage-class_8.cpp)]

##  <a name="onwizardfinish"></a>  CPropertyPage::OnWizardFinish

Cette fonction membre est appelée par le framework lorsque l’utilisateur clique sur le bouton Terminer de l’Assistant.

```
virtual BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la feuille de propriétés est détruite à la fin de l’Assistant ; Sinon, zéro.

### <a name="remarks"></a>Notes

Lorsqu’un utilisateur clique sur le **Terminer** bouton dans un Assistant, l’infrastructure appelle cette fonction ; lorsque `OnWizardFinish` retourne la valeur TRUE (valeur différente de zéro), la feuille de propriétés est en mesure d’être détruit (mais n’est pas détruit). Appelez `DestroyWindow` pour détruire la feuille de propriétés. N’appelez pas `DestroyWindow` de `OnWizardFinish`; cela entraîne une altération du tas ou autres erreurs.

Vous pouvez remplacer cette fonction membre pour spécifier une action de que l’utilisateur doit effectuer lorsque vous appuyez sur le bouton Terminer. Lors de la substitution de cette fonction, retourner FALSE pour empêcher que la feuille de propriétés en cours de destruction.

Pour plus d’informations sur les messages de notification envoyés lorsque l’utilisateur appuie sur le bouton Terminer dans une feuille de propriétés d’Assistant, consultez [PSN_WIZFINISH](/windows/desktop/Controls/psn-wizfinish) dans le SDK Windows.

Pour plus d’informations sur la façon de rendre une feuille de propriétés de type de l’Assistant, consultez [fonction CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#119](../../mfc/codesnippet/cpp/cpropertypage-class_9.cpp)]

[!code-cpp[NVC_MFCDocView#120](../../mfc/codesnippet/cpp/cpropertypage-class_10.cpp)]

[!code-cpp[NVC_MFCDocView#121](../../mfc/codesnippet/cpp/cpropertypage-class_11.cpp)]

[!code-cpp[NVC_MFCDocView#122](../../mfc/codesnippet/cpp/cpropertypage-class_12.cpp)]

##  <a name="onwizardnext"></a>  CPropertyPage::OnWizardNext

Cette fonction membre est appelée par le framework lorsque l’utilisateur clique sur le bouton suivant dans l’Assistant.

```
virtual LRESULT OnWizardNext();
```

### <a name="return-value"></a>Valeur de retour

0 pour passer automatiquement à la page suivante ; -1 pour empêcher la modification de la page. Pour accéder à une page différente de celle qui suit, retourner l’identificateur de la boîte de dialogue à afficher.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour spécifier une action de que l’utilisateur doit effectuer lorsque vous appuyez sur le bouton suivant.

Pour plus d’informations sur la façon de rendre une feuille de propriétés de type de l’Assistant, consultez [fonction CPropertySheet::SetWizardMode](../../mfc/reference/cpropertysheet-class.md#setwizardmode).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#123](../../mfc/codesnippet/cpp/cpropertypage-class_13.cpp)]

##  <a name="querysiblings"></a>  CPropertyPage::QuerySiblings

Appelez cette fonction membre pour transférer un message à chaque page dans la feuille de propriétés.

```
LRESULT QuerySiblings(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*wParam*<br/>
Spécifie des informations supplémentaires dépendant du message.

*lParam*<br/>
Spécifie des informations supplémentaires dépendant du message

### <a name="return-value"></a>Valeur de retour

La valeur différente de zéro à partir d’une page dans la feuille de propriétés, ou 0 si toutes les pages retournent la valeur 0.

### <a name="remarks"></a>Notes

Si une page retourne une valeur différente de zéro, la feuille de propriétés n’envoie pas le message pour les pages suivantes.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#124](../../mfc/codesnippet/cpp/cpropertypage-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#125](../../mfc/codesnippet/cpp/cpropertypage-class_15.cpp)]

[!code-cpp[NVC_MFCDocView#126](../../mfc/codesnippet/cpp/cpropertypage-class_16.cpp)]

##  <a name="setmodified"></a>  CPropertyPage::SetModified

Appelez cette fonction membre pour activer ou désactiver le bouton Appliquer, selon si les paramètres dans la page de propriétés doivent être appliquées à l’objet externe approprié.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Paramètres

*bChanged*<br/>
TRUE pour indiquer que les paramètres de page de propriété ont été modifiés depuis la dernière fois qu’ils ont été appliquées ; FALSE pour indiquer que les paramètres de page de propriété ont été appliqués, ou doivent être ignorées.

### <a name="remarks"></a>Notes

Le framework conserve la piste dont les pages sont « modifiées », autrement dit, les pages de propriétés pour lequel vous avez appelé `SetModified( TRUE )`. Il se peut que le bouton Appliquer sera toujours activé si vous appelez `SetModified( TRUE )` pour l’une des pages. Le bouton Appliquer va être désactivé lorsque vous appelez `SetModified( FALSE )` pour l’une des pages, mais uniquement si aucune des autres pages est « modifié ».

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#127](../../mfc/codesnippet/cpp/cpropertypage-class_17.cpp)]

## <a name="see-also"></a>Voir aussi

[MFC exemple CMNCTRL1](../../visual-cpp-samples.md)<br/>
[MFC exemple CMNCTRL2](../../visual-cpp-samples.md)<br/>
[Exemple MFC PROPDLG](../../visual-cpp-samples.md)<br/>
[Exemple MFC SNAPVW](../../visual-cpp-samples.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CPropertySheet, classe](../../mfc/reference/cpropertysheet-class.md)<br/>
[CDialog, classe](../../mfc/reference/cdialog-class.md)
