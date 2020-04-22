---
title: Classe CSnapInPropertyImpl
ms.date: 11/04/2016
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
ms.openlocfilehash: 3f09e8500eadd36eec53db95f10261834d672101
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747579"
---
# <a name="csnapinpropertypageimpl-class"></a>Classe CSnapInPropertyImpl

Cette classe fournit des méthodes pour la mise en œuvre d’un objet de page de propriété instantané.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyImpl](#csnapinpropertypageimpl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Modifie l’état des boutons **OK** et **Annuler.**|
|[CSnapInPropertyPageImpl::Créer](#create)|Initialise un objet `CSnapInPropertyPageImpl` nouvellement créé.|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Appelé par le cadre lorsque l’utilisateur clique sur le bouton **Apply Now** lors de l’utilisation d’une feuille de propriété de type assistant.|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Appelé par le cadre lorsque l’utilisateur clique sur le bouton **Aide** à l’aide d’une feuille de propriété de type assistant.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Appelé par le cadre lorsque la page actuelle n’est plus active.|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Appelé par le cadre lorsque l’utilisateur clique sur le bouton **Annuler** et avant l’annulation a eu lieu.|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Appelé par le cadre lorsque l’utilisateur clique sur le bouton **Reset** à l’aide d’une feuille de propriété de type assistant.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Appelé par le cadre lorsque la page actuelle devient active.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Appelé par le cadre lorsque l’utilisateur clique sur le bouton **Back** tout en utilisant une feuille de propriété de type assistant.|
|[CSnapInPropertyPageImpl:::OnWizardFinish](#onwizardfinish)|Appelé par le cadre lorsque l’utilisateur clique sur le bouton **Finition** à l’aide d’une feuille de propriété de type assistant.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Appelé par le cadre lorsque l’utilisateur clique sur le bouton **Suivant** à l’aide d’une feuille de propriété de type assistant.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Transmet le message actuel à toutes les pages de la feuille de propriété.|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Appelez pour activer ou désactiver le bouton **Apply Now.**|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|La `PROPSHEETPAGE` structure Windows `CSnapInPropertyPageImpl` utilisée par l’objet.|

## <a name="remarks"></a>Notes

`CSnapInPropertyPageImpl`fournit une implémentation de base pour un objet de page de propriété instantané. Les caractéristiques de base d’une page de propriété snap-in sont implémentées à l’aide de plusieurs interfaces différentes et types de cartes.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlsnap.h

## <a name="csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a>CSnapInPropertyPageImpl::CancelToClose

Appelez cette fonction après qu’un changement irrécupérable a été apporté aux données dans une page d’une feuille de propriété modale.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>Notes

Cette fonction modifiera le bouton **OK** pour **fermer** et désactiver le bouton **Annuler.** Cette modification avertit l’utilisateur qu’un changement est permanent et que les modifications ne peuvent pas être annulées.

La `CancelToClose` fonction membre ne fait rien dans une feuille de propriété sans mode, parce qu’une feuille de propriété sans mode n’a pas de bouton **Annuler** par défaut.

## <a name="csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a>CSnapInPropertyPageImpl::CSnapInPropertyImpl

Construit un objet `CSnapInPropertyPageImpl`.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszTitle (lpszTitle)*<br/>
[dans] Le titre de la page de propriété.

### <a name="remarks"></a>Notes

Pour initialiser la structure sous-jacente, appelez [CSnapInPropertyPageImpl::Create](#create).

## <a name="csnapinpropertypageimplcreate"></a><a name="create"></a>CSnapInPropertyPageImpl::Créer

Appelez cette fonction pour initialiser la structure sous-jacente de la page de propriété.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Valeur de retour

Une poignée `PROPSHEETPAGE` à une structure contenant les attributs de la feuille de propriété nouvellement créée.

### <a name="remarks"></a>Notes

Vous devez d’abord appeler [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl) avant d’appeler cette fonction.

## <a name="csnapinpropertypageimplm_psp"></a><a name="m_psp"></a>CSnapInPropertyPageImpl::m_psp

`m_psp`est une structure dont les `PROPSHEETPAGE`membres stockent les caractéristiques de .

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Notes

Utilisez cette structure pour initialiser l’apparence d’une page de propriété après sa construction.

Pour plus d’informations sur cette structure, y compris une liste de ses membres, voir [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) dans le SDK Windows.

## <a name="csnapinpropertypageimplonapply"></a><a name="onapply"></a>CSnapInPropertyPageImpl::OnApply

Cette fonction de membre est appelée lorsque l’utilisateur clique sur le **bouton OK** ou le bouton **Apply Now.**

```
BOOL OnApply();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les changements sont acceptés; sinon 0.

### <a name="remarks"></a>Notes

Avant `OnApply` peut être appelé par le `SetModified` cadre, vous devez avoir appelé et définir son paramètre à VRAI. Cela activera le bouton **Apply Now** dès que l’utilisateur effectue une modification sur la page de propriété.

Remplacez cette fonction de membre pour spécifier l’action que prend votre programme lorsque l’utilisateur clique sur le bouton **Apply Now.** Lors de la suppression, la fonction doit retourner TRUE pour accepter les modifications et FALSE pour empêcher les changements d’entrer en vigueur.

La mise `OnApply` en œuvre par défaut des retours TRUE.

## <a name="csnapinpropertypageimplonhelp"></a><a name="onhelp"></a>CSnapInPropertyPageImpl::OnHelp

Cette fonction de membre est appelée lorsque l’utilisateur clique sur le bouton **Aide** pour la page de propriété.

```cpp
void OnHelp();
```

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre pour afficher l’aide pour la page de propriété.

## <a name="csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a>CSnapInPropertyPageImpl::OnKillActive

Cette fonction de membre est appelée lorsque la page n’est plus la page active.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les données ont été mises à jour avec succès; sinon 0.

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre pour effectuer des tâches spéciales de validation des données.

## <a name="csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a>CSnapInPropertyPageImpl::OnQueryCancel

Cette fonction de membre est appelée lorsque l’utilisateur clique sur le bouton **Annuler** et avant que l’action d’annulation n’ait eu lieu.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valeur de retour

Nonzero pour permettre l’opération d’annulation; sinon 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction de membre pour spécifier une action que le programme prend lorsque l’utilisateur clique sur le bouton **Annuler.**

La mise `OnQueryCancel` en œuvre par défaut des retours TRUE.

## <a name="csnapinpropertypageimplonreset"></a><a name="onreset"></a>CSnapInPropertyPageImpl::OnReset

Cette fonction de membre s’appelle lorsque l’utilisateur clique sur le bouton **Annuler.**

```cpp
void OnReset();
```

### <a name="remarks"></a>Notes

Lorsque cette fonction est appelée, les modifications apportées à toutes les pages de propriété qui ont été faites par l’utilisateur qui clique déjà sur le bouton **Apply Now** sont jetées, et la feuille de propriété conserve la mise au point.

Remplacez cette fonction de membre pour spécifier l’action que prend le programme lorsque l’utilisateur clique sur le bouton **Annuler.**

## <a name="csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a>CSnapInPropertyPageImpl::OnSetActive

Cette fonction de membre est appelée lorsque la page est choisie par l’utilisateur et devient la page active.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la page a été définie avec succès actif; sinon 0.

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre pour effectuer des tâches lorsqu’une page est activée. Votre remplacement de cette fonction de membre devrait appeler la version par défaut avant tout autre traitement est fait.

La implémentation par défaut renvoie TRUE.

## <a name="csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a>CSnapInPropertyPageImpl::OnWizardBack

Cette fonction de membre est appelée lorsque l’utilisateur clique sur le bouton **Back** dans un assistant.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Valeur de retour

- 0 pour passer automatiquement à la page précédente.

- -1 pour empêcher la page de changer.

Pour sauter à une page autre que la suivante, retournez l’identifiant de la boîte de dialogue à afficher.

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre pour spécifier certaines mesures que l’utilisateur doit prendre lorsque le bouton **Back** est cliqué.

## <a name="csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a>CSnapInPropertyPageImpl:::OnWizardFinish

Cette fonction de membre est appelée lorsque l’utilisateur clique sur le bouton **Finition** dans un assistant.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la feuille de propriété est détruite lorsque l’assistant termine; autrement zéro.

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre pour spécifier certaines mesures que l’utilisateur doit prendre lorsque le bouton **Finition** est cliqué.

## <a name="csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a>CSnapInPropertyPageImpl::OnWizardNext

Cette fonction de membre est appelée lorsque l’utilisateur clique sur le bouton **Suivant** dans un assistant.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Valeur de retour

- 0 pour passer automatiquement à la page suivante.

- -1 pour empêcher la page de changer.

Pour sauter à une page autre que la suivante, retournez l’identifiant de la boîte de dialogue à afficher.

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre pour spécifier certaines mesures que l’utilisateur doit prendre lorsque le bouton **Suivant** est cliqué.

## <a name="csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a>CSnapInPropertyPageImpl::QuerySiblings

Appelez cette fonction membre pour transmettre un message à chaque page de la feuille de propriété.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*wParam*<br/>
[dans] Spécifie des informations supplémentaires dépendantes des messages.

*lParam*<br/>
[dans] Spécifie des informations supplémentaires dépendantes des messages.

### <a name="return-value"></a>Valeur de retour

Nonzero si le message ne doit pas être transmis à la page de propriété suivante; autrement zéro.

### <a name="remarks"></a>Notes

Si une page renvoie une valeur non zéro, la feuille de propriété n’envoie pas le message aux pages suivantes.

## <a name="csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a>CSnapInPropertyPageImpl::SetModified

Appelez cette fonction membre pour activer ou désactiver le bouton **Apply Now,** en fonction de la question de savoir si les paramètres de la page de propriété doivent être appliqués à l’objet externe approprié.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Paramètres

*b Modifié*<br/>
[dans] VRAI pour indiquer que les paramètres de la page de propriété ont été modifiés depuis la dernière fois qu’ils ont été appliqués; FALSE pour indiquer que les paramètres de la page de propriété ont été appliqués, ou doivent être ignorés.

### <a name="remarks"></a>Notes

La feuille de propriété garde une trace des pages qui sont `SetModified( TRUE )`«sales», c’est-à-dire, pages de propriété pour lesquelles vous avez appelé . Le bouton **Apply Now** sera toujours `SetModified( TRUE )` activé si vous appelez pour l’une des pages. Le bouton **Apply Now** sera `SetModified( FALSE )` désactivé lorsque vous appelez pour l’une des pages, mais seulement si aucune des autres pages n’est «sale».

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
