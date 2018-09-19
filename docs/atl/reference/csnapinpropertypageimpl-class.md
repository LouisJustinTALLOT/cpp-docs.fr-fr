---
title: Csnapinpropertypageimpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c89f577168593dcb22570af63801fc05654eb4b3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100681"
---
# <a name="csnapinpropertypageimpl-class"></a>Csnapinpropertypageimpl, classe

Cette classe fournit des méthodes pour implémenter un objet de page de propriétés de composant logiciel enfichable.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[CSnapInPropertyPageImpl::CancelToClose](#canceltoclose)|Modifie le statut de la **OK** et **Annuler** boutons.|
|[CSnapInPropertyPageImpl::Create](#create)|Initialise un nouvellement créé `CSnapInPropertyPageImpl` objet.|
|[CSnapInPropertyPageImpl::OnApply](#onapply)|Appelé par le framework lorsque l’utilisateur clique sur le **appliquer maintenant** bouton lors de l’utilisation d’une feuille de propriétés de type de l’Assistant.|
|[CSnapInPropertyPageImpl::OnHelp](#onhelp)|Appelé par le framework lorsque l’utilisateur clique sur le **aide** bouton lors de l’utilisation d’une feuille de propriétés de type de l’Assistant.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|Appelé par le framework lorsque la page actuelle n’est plus active.|
|[CSnapInPropertyPageImpl::OnQueryCancel](#onquerycancel)|Appelé par le framework lorsque l’utilisateur clique sur le **Annuler** bouton et avant l’annulation a eu lieu.|
|[CSnapInPropertyPageImpl::OnReset](#onreset)|Appelé par le framework lorsque l’utilisateur clique sur le **réinitialiser** bouton lors de l’utilisation d’une feuille de propriétés de type de l’Assistant.|
|[CSnapInPropertyPageImpl::OnSetActive](#onsetactive)|Appelé par le framework lorsque la page actuelle devient active.|
|[CSnapInPropertyPageImpl::OnWizardBack](#onwizardback)|Appelé par le framework lorsque l’utilisateur clique sur le **retour** bouton lors de l’utilisation d’une feuille de propriétés de type de l’Assistant.|
|[CSnapInPropertyPageImpl::OnWizardFinish](#onwizardfinish)|Appelé par le framework lorsque l’utilisateur clique sur le **Terminer** bouton lors de l’utilisation d’une feuille de propriétés de type de l’Assistant.|
|[CSnapInPropertyPageImpl::OnWizardNext](#onwizardnext)|Appelé par le framework lorsque l’utilisateur clique sur le **suivant** bouton lors de l’utilisation d’une feuille de propriétés de type de l’Assistant.|
|[CSnapInPropertyPageImpl::QuerySiblings](#querysiblings)|Transfère le message en cours à toutes les pages de la feuille de propriétés.|
|[CSnapInPropertyPageImpl::SetModified](#setmodified)|Appel pour activer ou désactiver la **appliquer maintenant** bouton.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CSnapInPropertyPageImpl::m_psp](#m_psp)|Le Windows `PROPSHEETPAGE` structure utilisée par le `CSnapInPropertyPageImpl` objet.|

## <a name="remarks"></a>Notes

`CSnapInPropertyPageImpl` Fournit une implémentation de base pour un objet de page de propriété du composant logiciel enfichable. Les fonctionnalités de base d’une page de propriétés du composant logiciel enfichable sont implémentées à l’aide de plusieurs interfaces différentes et mappent les types.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsnap.h

##  <a name="canceltoclose"></a>  CSnapInPropertyPageImpl::CancelToClose

Appelez cette fonction après qu’une modification irrécupérable a été apportée aux données dans une page d’une feuille de propriétés modale.

```
void CancelToClose();
```

### <a name="remarks"></a>Notes

Cette fonction changera la **OK** bouton à **fermer** et désactiver la **Annuler** bouton. Modifier les alertes de l’utilisateur qu’une modification est définitive et les modifications ne peut pas être annulée.

Le `CancelToClose` fonction membre ne fait rien dans une feuille de propriétés non modale, car une feuille de propriétés non modale n’a pas un **Annuler** bouton par défaut.

##  <a name="csnapinpropertypageimpl"></a>  CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

Construit un objet `CSnapInPropertyPageImpl`.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszTitle*<br/>
[in] Le titre de la page de propriétés.

### <a name="remarks"></a>Notes

Pour initialiser la structure sous-jacente, appelez [CSnapInPropertyPageImpl::Create](#create).

##  <a name="create"></a>  CSnapInPropertyPageImpl::Create

Appelez cette fonction pour initialiser la structure sous-jacente de la page de propriétés.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>Valeur de retour

Un handle vers un `PROPSHEETPAGE` structure contenant les attributs de la feuille de propriétés nouvellement créé.

### <a name="remarks"></a>Notes

Vous devez d’abord appeler [CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl) avant d’appeler cette fonction.

##  <a name="m_psp"></a>  CSnapInPropertyPageImpl::m_psp

`m_psp` est une structure dont les membres stockent les caractéristiques de `PROPSHEETPAGE`.

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>Notes

Utilisez cette structure pour initialiser l’apparence d’une page de propriétés après sa construction.

Pour plus d’informations sur cette structure, y compris une liste de ses membres, consultez [PROPSHEETPAGE](https://msdn.microsoft.com/library/aa815151) dans le SDK Windows.

##  <a name="onapply"></a>  CSnapInPropertyPageImpl::OnApply

Cette fonction membre est appelée lorsque l’utilisateur clique sur le **OK** ou **appliquer maintenant** bouton.

```
BOOL OnApply();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les modifications sont acceptées ; sinon 0.

### <a name="remarks"></a>Notes

Avant de `OnApply` peut être appelée par l’infrastructure, vous devez appeler `SetModified` et son paramètre la valeur TRUE. Cela activera le **appliquer maintenant** bouton dès que l’utilisateur apporte une modification sur la page de propriétés.

Remplacez cette fonction membre pour spécifier l’action prise par votre programme lorsque l’utilisateur clique sur le **appliquer maintenant** bouton. Lors de la substitution, la fonction doit retourner TRUE pour accepter les modifications et FALSE pour empêcher les modifications de prendre effet.

L’implémentation par défaut de `OnApply` retourne la valeur TRUE.

##  <a name="onhelp"></a>  CSnapInPropertyPageImpl::OnHelp

Cette fonction membre est appelée lorsque l’utilisateur clique sur le **aide** bouton de la page de propriétés.

```
void OnHelp();
```

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour afficher l’aide de la page de propriétés.

##  <a name="onkillactive"></a>  CSnapInPropertyPageImpl::OnKillActive

Cette fonction membre est appelée lorsque la page n’est plus la page active.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les données a été mises à jour ; sinon 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour effectuer des tâches de validation de données spéciaux.

##  <a name="onquerycancel"></a>  CSnapInPropertyPageImpl::OnQueryCancel

Cette fonction membre est appelée lorsque l’utilisateur clique sur le **Annuler** bouton et avant l’annulation action a eu lieu.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro pour autoriser l’opération d’annulation ; sinon 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour spécifier une action que le programme prend lorsque l’utilisateur clique sur le **Annuler** bouton.

L’implémentation par défaut de `OnQueryCancel` retourne la valeur TRUE.

##  <a name="onreset"></a>  CSnapInPropertyPageImpl::OnReset

Cette fonction membre est appelée lorsque l’utilisateur clique sur le **Annuler** bouton.

```
void OnReset();
```

### <a name="remarks"></a>Notes

Lorsque cette fonction est appelée, les modifications à toutes les pages de propriétés qui ont été apportées par l’utilisateur précédemment en cliquant sur le **appliquer maintenant** bouton sont ignorés, et la feuille de propriétés conserve le focus.

Remplacez cette fonction membre pour spécifier l’action que le programme prend lorsque l’utilisateur clique sur le **Annuler** bouton.

##  <a name="onsetactive"></a>  CSnapInPropertyPageImpl::OnSetActive

Cette fonction membre est appelée lorsque la page est choisie par l’utilisateur et devient la page active.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la page a été définie correctement active ; sinon 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour effectuer des tâches lorsqu’une page est activée. La substitution de cette fonction membre doit appeler la version par défaut avant que tout autre traitement soit effectué.

L’implémentation par défaut retourne la valeur TRUE.

##  <a name="onwizardback"></a>  CSnapInPropertyPageImpl::OnWizardBack

Cette fonction membre est appelée lorsque l’utilisateur clique sur le **retour** bouton dans un Assistant.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>Valeur de retour

- 0 pour passer automatiquement à la page précédente.

- -1 pour empêcher la modification de la page.

Pour accéder à une page différente de celle qui suit, retourner l’identificateur de la boîte de dialogue à afficher.

### <a name="remarks"></a>Notes

Remplacer cette fonction membre pour spécifier une action de l’utilisateur doit effectuer lorsque le **retour** bouton.

##  <a name="onwizardfinish"></a>  CSnapInPropertyPageImpl::OnWizardFinish

Cette fonction membre est appelée lorsque l’utilisateur clique sur le **Terminer** bouton dans un Assistant.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la feuille de propriétés est détruite à la fin de l’Assistant ; Sinon, zéro.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour spécifier une action de l’utilisateur doit effectuer lorsque le **Terminer** bouton.

##  <a name="onwizardnext"></a>  CSnapInPropertyPageImpl::OnWizardNext

Cette fonction membre est appelée lorsque l’utilisateur clique sur le **suivant** bouton dans un Assistant.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>Valeur de retour

- 0 pour passer automatiquement à la page suivante.

- -1 pour empêcher la modification de la page.

Pour accéder à une page différente de celle qui suit, retourner l’identificateur de la boîte de dialogue à afficher.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre pour spécifier une action de l’utilisateur doit effectuer lorsque le **suivant** bouton.

##  <a name="querysiblings"></a>  CSnapInPropertyPageImpl::QuerySiblings

Appelez cette fonction membre pour transférer un message à chaque page dans la feuille de propriétés.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

*wParam*<br/>
[in] Spécifie des informations supplémentaires dépendant du message.

*lParam*<br/>
[in] Spécifie des informations supplémentaires dépendant du message.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le message ne doit pas être transféré à la page suivante de la propriété ; Sinon, zéro.

### <a name="remarks"></a>Notes

Si une page retourne une valeur différente de zéro, la feuille de propriétés n’envoie pas le message pour les pages suivantes.

##  <a name="setmodified"></a>  CSnapInPropertyPageImpl::SetModified

Appelez cette fonction membre pour activer ou désactiver la **appliquer maintenant** bouton, en fonction de si les paramètres dans la page de propriétés doivent être appliquées à l’objet externe approprié.

```
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>Paramètres

*bChanged*<br/>
[in] TRUE pour indiquer que les paramètres de page de propriété ont été modifiés depuis la dernière fois qu’ils ont été appliquées ; FALSE pour indiquer que les paramètres de page de propriété ont été appliqués, ou doivent être ignorées.

### <a name="remarks"></a>Notes

La feuille de propriétés conserve la piste dont les pages sont « modifiées », autrement dit, les pages de propriétés pour lequel vous avez appelé `SetModified( TRUE )`. Le **appliquer maintenant** bouton est toujours activé si vous appelez `SetModified( TRUE )` pour l’une des pages. Le **appliquer maintenant** bouton est désactivé lorsque vous appelez `SetModified( FALSE )` pour l’une des pages, mais uniquement si aucune des autres pages est « modifié ».

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
