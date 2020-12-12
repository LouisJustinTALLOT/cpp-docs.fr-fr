---
description: 'En savoir plus sur : classe CSnapInPropertyPageImpl'
title: CSnapInPropertyPageImpl, classe
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
ms.openlocfilehash: c3699dff31291525638f128382ad39369f18deca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140541"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl, classe

Cette classe fournit des méthodes pour implémenter un objet de page de propriétés de composant logiciel enfichable.

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
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Modifie l’état des boutons **OK** et **Annuler** .|
|[CSnapInPropertyPageImpl :: Create](#create)|Initialise un objet nouvellement créé `CSnapInPropertyPageImpl` .|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Appelée par l’infrastructure quand l’utilisateur clique sur le bouton **appliquer maintenant** tout en utilisant une feuille de propriétés de type assistant.|
|[CSnapInPropertyPageImpl :: OnHelp](#onhelp)|Appelée par l’infrastructure quand l’utilisateur clique sur le bouton **aide** lors de l’utilisation d’une feuille de propriétés de type assistant.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Appelé par le Framework lorsque la page active n’est plus active.|
|[CSnapInPropertyPageImpl :: OnQueryCancel](#onquerycancel)|Appelée par l’infrastructure quand l’utilisateur clique sur le bouton **Annuler** et avant que l’annulation ait eu lieu.|
|[CSnapInPropertyPageImpl :: OnReset](#onreset)|Appelée par l’infrastructure quand l’utilisateur clique sur le bouton **Réinitialiser** lors de l’utilisation d’une feuille de propriétés de type assistant.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Appelé par le Framework lorsque la page active devient active.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Appelée par l’infrastructure quand l’utilisateur clique sur le bouton **précédent** lors de l’utilisation d’une feuille de propriétés de type assistant.|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Appelée par l’infrastructure quand l’utilisateur clique sur le bouton **Terminer** lors de l’utilisation d’une feuille de propriétés de type assistant.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Appelée par l’infrastructure quand l’utilisateur clique sur le bouton **suivant** lors de l’utilisation d’une feuille de propriétés de type assistant.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Transfère le message actuel à toutes les pages de la feuille de propriétés.|
|[CSnapInPropertyPageImpl :: SetModified](#setmodified)|Appelez pour activer ou désactiver le bouton **appliquer maintenant** .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CSnapInPropertyPageImpl :: m_psp](#m_psp)|Structure Windows `PROPSHEETPAGE` utilisée par l' `CSnapInPropertyPageImpl` objet.|

## <a name="remarks"></a>Notes

`CSnapInPropertyPageImpl` fournit une implémentation de base pour un objet de page de propriétés de composant logiciel enfichable. Les fonctionnalités de base d’une page de propriétés de composant logiciel enfichable sont implémentées à l’aide de différentes interfaces et types de mappages.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlsnap. h

## <a name="csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a> CSnapInPropertyPageImpl::CancelToClose

Appelez cette fonction après qu’une modification irrécupérable a été apportée aux données dans une page d’une feuille de propriétés modale.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>Notes

Cette fonction modifie le bouton **OK** pour **Fermer** et désactiver le bouton **Annuler** . Cette modification avertit l’utilisateur qu’une modification est définitive et que les modifications ne peuvent pas être annulées.

La `CancelToClose` fonction membre ne fait rien dans une feuille de propriétés non modale, car une feuille de propriétés non modale n’a pas de bouton **Annuler** par défaut.

## <a name="csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a> CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

Construit un objet `CSnapInPropertyPageImpl`.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszTitle*<br/>
dans Titre de la page de propriétés.

### <a name="remarks"></a>Notes

Pour initialiser la structure sous-jacente, appelez [CSnapInPropertyPageImpl :: Create](#create).

## <a name="csnapinpropertypageimplcreate"></a><a name="create"></a> CSnapInPropertyPageImpl :: Create

Appelez cette fonction pour initialiser la structure sous-jacente de la page de propriétés.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Valeur renvoyée

Handle d’une `PROPSHEETPAGE` structure contenant les attributs de la feuille de propriétés nouvellement créée.

### <a name="remarks"></a>Notes

Vous devez d’abord appeler [CSnapInPropertyPageImpl :: CSnapInPropertyPageImpl](#csnapinpropertypageimpl) avant d’appeler cette fonction.

## <a name="csnapinpropertypageimplm_psp"></a><a name="m_psp"></a> CSnapInPropertyPageImpl :: m_psp

`m_psp` est une structure dont les membres stockent les caractéristiques de `PROPSHEETPAGE` .

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Notes

Utilisez cette structure pour initialiser l’apparence d’une page de propriétés après qu’elle a été construite.

Pour plus d’informations sur cette structure, y compris la liste de ses membres, consultez [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) dans le SDK Windows.

## <a name="csnapinpropertypageimplonapply"></a><a name="onapply"></a> CSnapInPropertyPageImpl::OnApply

Cette fonction membre est appelée quand l’utilisateur clique sur le bouton **OK** ou **appliquer maintenant** .

```
BOOL OnApply();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si les modifications sont acceptées ; Sinon, 0.

### <a name="remarks"></a>Notes

Avant de `OnApply` pouvoir être appelé par l’infrastructure, vous devez avoir appelé `SetModified` et défini son paramètre sur true. Cette opération active le bouton **appliquer maintenant** dès que l’utilisateur apporte une modification dans la page de propriétés.

Substituez cette fonction membre pour spécifier l’action que votre programme prend lorsque l’utilisateur clique sur le bouton **appliquer maintenant** . Lors de la substitution, la fonction doit retourner TRUE pour accepter les modifications et FALSe pour empêcher que les modifications prennent effet.

L’implémentation par défaut de `OnApply` retourne la valeur true.

## <a name="csnapinpropertypageimplonhelp"></a><a name="onhelp"></a> CSnapInPropertyPageImpl :: OnHelp

Cette fonction membre est appelée quand l’utilisateur clique sur le bouton **aide** pour la page de propriétés.

```cpp
void OnHelp();
```

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour afficher l’aide de la page de propriétés.

## <a name="csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a> CSnapInPropertyPageImpl::OnKillActive

Cette fonction membre est appelée lorsque la page n’est plus la page active.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si les données ont été correctement mises à jour ; Sinon, 0.

### <a name="remarks"></a>Notes

Substituez cette fonction membre pour effectuer des tâches de validation de données spéciales.

## <a name="csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a> CSnapInPropertyPageImpl :: OnQueryCancel

Cette fonction membre est appelée quand l’utilisateur clique sur le bouton **Annuler** et avant que l’action d’annulation ait eu lieu.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro pour autoriser l’opération d’annulation ; Sinon, 0.

### <a name="remarks"></a>Notes

Substituez cette fonction membre pour spécifier une action que le programme prend lorsque l’utilisateur clique sur le bouton **Annuler** .

L’implémentation par défaut de `OnQueryCancel` retourne la valeur true.

## <a name="csnapinpropertypageimplonreset"></a><a name="onreset"></a> CSnapInPropertyPageImpl :: OnReset

Cette fonction membre est appelée quand l’utilisateur clique sur le bouton **Annuler** .

```cpp
void OnReset();
```

### <a name="remarks"></a>Notes

Lorsque cette fonction est appelée, les modifications apportées à toutes les pages de propriétés qui ont été effectuées par l’utilisateur précédemment en cliquant sur le bouton **appliquer maintenant** sont ignorées, et la feuille de propriétés conserve le focus.

Substituez cette fonction membre pour spécifier l’action prise par le programme lorsque l’utilisateur clique sur le bouton **Annuler** .

## <a name="csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a> CSnapInPropertyPageImpl::OnSetActive

Cette fonction membre est appelée lorsque la page est choisie par l’utilisateur et devient la page active.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la page a été correctement définie ; Sinon, 0.

### <a name="remarks"></a>Notes

Substituez cette fonction membre pour effectuer des tâches lorsqu’une page est activée. Votre remplacement de cette fonction membre doit appeler la version par défaut avant que tout autre traitement ne soit effectué.

L’implémentation par défaut retourne la valeur TRUE.

## <a name="csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a> CSnapInPropertyPageImpl::OnWizardBack

Cette fonction membre est appelée quand l’utilisateur clique sur le bouton **précédent** dans un Assistant.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Valeur renvoyée

- 0 pour avancer automatiquement jusqu’à la page précédente.

- -1 pour empêcher la modification de la page.

Pour accéder à une page autre que la suivante, renvoyez l’identificateur de la boîte de dialogue à afficher.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour spécifier une action que l’utilisateur doit effectuer lorsque l’utilisateur clique sur le bouton **précédent** .

## <a name="csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a> CSnapInPropertyPageImpl::OnWizardFinish

Cette fonction membre est appelée quand l’utilisateur clique sur le bouton **Terminer** dans un Assistant.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la feuille de propriétés est détruite à la fin de l’Assistant ; Sinon, zéro.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour spécifier une action que l’utilisateur doit effectuer lorsque l’utilisateur clique sur le bouton **Terminer** .

## <a name="csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a> CSnapInPropertyPageImpl::OnWizardNext

Cette fonction membre est appelée quand l’utilisateur clique sur le bouton **suivant** dans un Assistant.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Valeur renvoyée

- 0 pour passer automatiquement à la page suivante.

- -1 pour empêcher la modification de la page.

Pour accéder à une page autre que la suivante, renvoyez l’identificateur de la boîte de dialogue à afficher.

### <a name="remarks"></a>Notes

Substituez cette fonction membre pour spécifier une action que l’utilisateur doit effectuer lorsqu’un clic est effectué sur le bouton **suivant** .

## <a name="csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a> CSnapInPropertyPageImpl::QuerySiblings

Appelez cette fonction membre pour transférer un message à chaque page de la feuille de propriétés.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*wParam*<br/>
dans Spécifie des informations supplémentaires dépendantes du message.

*lParam*<br/>
dans Spécifie des informations supplémentaires dépendantes du message.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le message ne doit pas être transmis à la page de propriétés suivante ; Sinon, zéro.

### <a name="remarks"></a>Notes

Si une page retourne une valeur différente de zéro, la feuille de propriétés n’envoie pas le message aux pages suivantes.

## <a name="csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a> CSnapInPropertyPageImpl :: SetModified

Appelez cette fonction membre pour activer ou désactiver le bouton **appliquer maintenant** , selon que les paramètres de la page de propriétés doivent être appliqués à l’objet externe approprié.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Paramètres

*bChanged*<br/>
dans TRUE pour indiquer que les paramètres de la page de propriétés ont été modifiés depuis la dernière application. FALSe pour indiquer que les paramètres de la page de propriétés ont été appliqués ou doivent être ignorés.

### <a name="remarks"></a>Notes

La feuille de propriétés assure le suivi des pages qui sont « modifiées », c’est-à-dire des pages de propriétés pour lesquelles vous avez appelé `SetModified( TRUE )` . Le bouton **appliquer maintenant** sera toujours activé si vous appelez `SetModified( TRUE )` pour l’une des pages. Le bouton **appliquer maintenant** est désactivé lorsque vous appelez `SetModified( FALSE )` pour l’une des pages, mais uniquement si aucune autre page n’est « modifiée ».

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
