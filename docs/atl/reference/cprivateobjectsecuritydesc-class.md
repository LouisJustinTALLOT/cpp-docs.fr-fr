---
title: Classe CPrivateObjectSecurityDesc
ms.date: 11/04/2016
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
ms.openlocfilehash: 2fcfdfecab649b571047613ec0889b02d2c7a7a0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331410"
---
# <a name="cprivateobjectsecuritydesc-class"></a>Classe CPrivateObjectSecurityDesc

Cette classe représente un objet descripteur de sécurité d’objets privés.

## <a name="syntax"></a>Syntaxe

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPrivateObjectSecurityDesc:::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|Constructeur.|
|[CPrivateObjectSecurityDesc::-CPrivateObjectSecurityDesc](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Appelez cette méthode pour convertir un descripteur de sécurité et ses listes de contrôle d’accès (ACL) en un format qui prend en charge la propagation automatique des entrées héréditaires de contrôle d’accès (ACE).|
|[CPrivateObjectSecurityDesc::Créer](#create)|Appelez cette méthode pour allouer et initialiser un descripteur de sécurité auto-relatif pour l’objet privé créé par le gestionnaire de ressources d’appel.|
|[CPrivateObjectSecurityDesc::Get](#get)|Appelez cette méthode pour récupérer des informations du descripteur de sécurité d’un objet privé.|
|[CPrivateObjectSecurityDesc::Set](#set)|Appelez cette méthode pour modifier le descripteur de sécurité d’un objet privé.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[opérateur](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Cette classe, dérivée de [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), fournit des méthodes pour créer et gérer le descripteur de sécurité d’un objet privé.

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="cprivateobjectsecuritydescconverttoautoinherit"></a><a name="converttoautoinherit"></a>CPrivateObjectSecurityDesc::ConvertToAutoInherit

Appelez cette méthode pour convertir un descripteur de sécurité et ses listes de contrôle d’accès (ACL) en un format qui prend en charge la propagation automatique des entrées héréditaires de contrôle d’accès (ACE).

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
Pointeur vers un objet [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) faisant référence au contenant parent de l’objet. S’il n’y a pas de contenant parent, ce paramètre est NULL.

*Objecttype*<br/>
Pointeur `GUID` vers une structure qui identifie le type d’objet associé à l’objet actuel. Définissez *ObjectType* à NULL si l’objet n’a pas de GUID.

*bIsDirectoryObject*<br/>
Précise si le nouvel objet peut contenir d’autres objets. Une valeur de vrai indique que le nouvel objet est un conteneur. Une valeur de faux indique que le nouvel objet n’est pas un conteneur.

*GenericMapping*<br/>
Pointeur vers une structure [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) qui spécifie la cartographie de chaque droit générique à des droits spécifiques pour l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Cette méthode tente de déterminer si les CEA de la liste discrétionnaire de contrôle de l’accès (DACL) et la liste de contrôle d’accès au système (SACL) du descripteur de sécurité actuel ont été hérités du descripteur de sécurité parent. Il appelle la fonction [ConvertToAutoInheritPrivateObjectSecurity.](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity)

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc:::CPrivateObjectSecurityDesc

Constructeur.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Notes

Initialise l'objet `CPrivateObjectSecurityDesc`.

## <a name="cprivateobjectsecuritydesccprivateobjectsecuritydesc"></a><a name="dtor"></a>CPrivateObjectSecurityDesc::-CPrivateObjectSecurityDesc

Destructeur.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources allouées et supprime le descripteur de sécurité de l’objet privé.

## <a name="cprivateobjectsecuritydesccreate"></a><a name="create"></a>CPrivateObjectSecurityDesc::Créer

Appelez cette méthode pour allouer et initialiser un descripteur de sécurité auto-relatif pour l’objet privé créé par le gestionnaire de ressources d’appel.

```
bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
Pointeur vers un objet [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) faisant référence à l’annuaire parent dans lequel un nouvel objet est en cours de création. Réglez à NULL s’il n’y a pas d’annuaire parent.

*pCreator (en anglais)*<br/>
Pointeur vers un descripteur de sécurité fourni par le créateur de l’objet. Si le créateur de l’objet ne transmet pas explicitement les informations de sécurité du nouvel objet, définissez ce paramètre à NULL.

*bIsDirectoryObject*<br/>
Précise si le nouvel objet peut contenir d’autres objets. Une valeur de vrai indique que le nouvel objet est un conteneur. Une valeur de faux indique que le nouvel objet n’est pas un conteneur.

*par jeton*<br/>
Référence à [l’objet CAccessToken](../../atl/reference/caccesstoken-class.md) pour le processus client au nom de l’objet en cours de création.

*GenericMapping*<br/>
Pointeur vers une structure [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) qui spécifie la cartographie de chaque droit générique à des droits spécifiques pour l’objet.

*Objecttype*<br/>
Pointeur `GUID` vers une structure qui identifie le type d’objet associé à l’objet actuel. Définissez *ObjectType* à NULL si l’objet n’a pas de GUID.

*bIsContainerObject*<br/>
Précise si le nouvel objet peut contenir d’autres objets. Une valeur de vrai indique que le nouvel objet est un conteneur. Une valeur de faux indique que le nouvel objet n’est pas un conteneur.

*AutoInheritFlags*<br/>
Un ensemble de drapeaux bits qui contrôlent la façon dont les entrées de contrôle d’accès (ACE) sont héritées de *pParent*. Voir [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) pour plus de détails.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Cette méthode appelle [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) ou [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex).

La deuxième méthode permet de spécifier le type d’objet GUID du nouvel objet ou de contrôler l’héritage des ACE.

> [!NOTE]
> Un descripteur de sécurité auto-relatif est un descripteur de sécurité qui stocke toutes ses informations de sécurité dans un bloc de mémoire contigus.

## <a name="cprivateobjectsecuritydescget"></a><a name="get"></a>CPrivateObjectSecurityDesc::Get

Appelez cette méthode pour récupérer des informations du descripteur de sécurité d’un objet privé.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Paramètres

*si*<br/>
Un ensemble de drapeaux bits qui indiquent les parties du descripteur de sécurité à récupérer. Cette valeur peut être [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) une combinaison des SECURITY_INFORMATION drapeaux bits.

*pResult*<br/>
Pointeur vers un objet [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) qui reçoit une copie des informations demandées du descripteur de sécurité spécifié.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Le descripteur de sécurité est une structure et des données associées qui contiennent les informations de sécurité d’un objet titrable.

## <a name="cprivateobjectsecuritydescoperator-"></a><a name="operator_eq"></a>CPrivateObjectSecurityDesc::opérateur

Opérateur d'assignation.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
Objet `CPrivateObjectSecurityDesc` à assigner à l'objet actif.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet mis à jour. `CPrivateObjectSecurityDesc`

## <a name="cprivateobjectsecuritydescset"></a><a name="set"></a>CPrivateObjectSecurityDesc::Set

Appelez cette méthode pour modifier le descripteur de sécurité d’un objet privé.

```
bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```

### <a name="parameters"></a>Paramètres

*si*<br/>
Un ensemble de drapeaux bits qui indiquent les parties du descripteur de sécurité à définir. Cette valeur peut être [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) une combinaison des SECURITY_INFORMATION drapeaux bits.

*Modification*<br/>
Pointeur vers un objet [CSecurityDesc.](../../atl/reference/csecuritydesc-class.md) Les parties de ce descripteur de sécurité indiquées par le paramètre *si* sont appliquées au descripteur de sécurité de l’objet.

*GenericMapping*<br/>
Pointeur vers une structure [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) qui spécifie la cartographie de chaque droit générique à des droits spécifiques pour l’objet.

*par jeton*<br/>
Référence à [l’objet CAccessToken](../../atl/reference/caccesstoken-class.md) pour le processus client au nom de l’objet en cours de création.

*AutoInheritFlags*<br/>
Un ensemble de drapeaux bits qui contrôlent la façon dont les entrées de contrôle d’accès (ACE) sont héritées de *pParent*. Voir [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) pour plus de détails.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

La deuxième méthode permet de spécifier le type d’objet GUID de l’objet ou de contrôler l’héritage des ACE.

## <a name="see-also"></a>Voir aussi

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)<br/>
[Classe CSecurityDesc](../../atl/reference/csecuritydesc-class.md)
