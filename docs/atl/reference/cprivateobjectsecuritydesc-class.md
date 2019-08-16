---
title: CPrivateObjectSecurityDesc, classe
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
ms.openlocfilehash: 97ea2b8411b404caf9f833ad85f226d18aea1e73
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496579"
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc, classe

Cette classe représente un objet de descripteur de sécurité d’objet privé.

## <a name="syntax"></a>Syntaxe

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|Constructeur.|
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Appelez cette méthode pour convertir un descripteur de sécurité et ses listes de contrôle d’accès (ACL) en un format qui prend en charge la propagation automatique des entrées de contrôle d’accès (ACE) pouvant être héritées.|
|[CPrivateObjectSecurityDesc::Create](#create)|Appelez cette méthode pour allouer et initialiser un descripteur de sécurité auto-relatif pour l’objet privé créé par le gestionnaire de ressources appelant.|
|[CPrivateObjectSecurityDesc::Get](#get)|Appelez cette méthode pour récupérer des informations à partir du descripteur de sécurité d’un objet privé.|
|[CPrivateObjectSecurityDesc::Set](#set)|Appelez cette méthode pour modifier le descripteur de sécurité d’un objet privé.|

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator =](#operator_eq)|Opérateur d'assignation.|

## <a name="remarks"></a>Notes

Cette classe, dérivée de [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), fournit des méthodes pour créer et gérer le descripteur de sécurité d’un objet privé.

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Configuration requise

**En-tête:** ATLSecurity. h

##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit

Appelez cette méthode pour convertir un descripteur de sécurité et ses listes de contrôle d’accès (ACL) en un format qui prend en charge la propagation automatique des entrées de contrôle d’accès (ACE) pouvant être héritées.

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
Pointeur vers un objet [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) qui référence le conteneur parent de l’objet. S’il n’existe aucun conteneur parent, ce paramètre a la valeur NULL.

*ObjectType*<br/>
Pointeur vers une `GUID` structure qui identifie le type d’objet associé à l’objet en cours. Affectez à *ObjectType* la valeur null si l’objet n’a pas de GUID.

*bIsDirectoryObject*<br/>
Spécifie si le nouvel objet peut contenir d’autres objets. La valeur true indique que le nouvel objet est un conteneur. La valeur false indique que le nouvel objet n’est pas un conteneur.

*GenericMapping*<br/>
Pointeur vers une structure [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) qui spécifie le mappage de chaque droit générique à des droits spécifiques pour l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Cette méthode tente de déterminer si les ACE de la liste de contrôle d’accès discrétionnaire (DACL) et de la liste de contrôle d’accès système (SACL) du descripteur de sécurité actuel ont été héritées du descripteur de sécurité parent. Il appelle la fonction [ConvertToAutoInheritPrivateObjectSecurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) .

##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

Constructeur.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Notes

Initialise l' `CPrivateObjectSecurityDesc` objet.

##  <a name="dtor"></a>  CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc

Destructeur.

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Notes

Le destructeur libère toutes les ressources allouées et supprime le descripteur de sécurité de l’objet privé.

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

Appelez cette méthode pour allouer et initialiser un descripteur de sécurité auto-relatif pour l’objet privé créé par le gestionnaire de ressources appelant.

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
Pointeur vers un objet [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) référençant le répertoire parent dans lequel un nouvel objet est créé. Affectez la valeur NULL s’il n’existe aucun répertoire parent.

*pCreator*<br/>
Pointeur vers un descripteur de sécurité fourni par le créateur de l’objet. Si le créateur de l’objet ne transmet pas explicitement les informations de sécurité pour le nouvel objet, attribuez la valeur NULL à ce paramètre.

*bIsDirectoryObject*<br/>
Spécifie si le nouvel objet peut contenir d’autres objets. La valeur true indique que le nouvel objet est un conteneur. La valeur false indique que le nouvel objet n’est pas un conteneur.

*Lexical*<br/>
Référence à l’objet [caccesstoken,](../../atl/reference/caccesstoken-class.md) pour le processus client au nom duquel l’objet est créé.

*GenericMapping*<br/>
Pointeur vers une structure [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) qui spécifie le mappage de chaque droit générique à des droits spécifiques pour l’objet.

*ObjectType*<br/>
Pointeur vers une `GUID` structure qui identifie le type d’objet associé à l’objet en cours. Affectez à *ObjectType* la valeur null si l’objet n’a pas de GUID.

*bIsContainerObject*<br/>
Spécifie si le nouvel objet peut contenir d’autres objets. La valeur true indique que le nouvel objet est un conteneur. La valeur false indique que le nouvel objet n’est pas un conteneur.

*AutoInheritFlags*<br/>
Jeu d’indicateurs de bits qui contrôlent la façon dont les entrées de contrôle d’accès (ACE) sont héritées de *pParent*. Pour plus d’informations, consultez [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) .

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Cette méthode appelle [CreatePrivateObjectSercurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) ou [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex).

La deuxième méthode permet de spécifier le GUID du type d’objet du nouvel objet ou de contrôler la façon dont les ACE sont héritées.

> [!NOTE]
>  Un descripteur de sécurité auto-relatif est un descripteur de sécurité qui stocke toutes ses informations de sécurité dans un bloc de mémoire contigu.

##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get

Appelez cette méthode pour récupérer des informations à partir du descripteur de sécurité d’un objet privé.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Paramètres

*si*<br/>
Jeu d’indicateurs binaires qui indiquent les parties du descripteur de sécurité à récupérer. Cette valeur peut être une combinaison des indicateurs de bits [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) .

*pResult*<br/>
Pointeur vers un objet [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) qui reçoit une copie des informations demandées à partir du descripteur de sécurité spécifié.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

Le descripteur de sécurité est une structure et des données associées qui contiennent les informations de sécurité pour un objet sécurisable.

##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =

Opérateur d'assignation.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Paramètres

*rhs*<br/>
`CPrivateObjectSecurityDesc` Objet à assigner à l’objet actuel.

### <a name="return-value"></a>Valeur de retour

Retourne l’objet `CPrivateObjectSecurityDesc` mis à jour.

##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set

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
Jeu d’indicateurs binaires qui indiquent les parties du descripteur de sécurité à définir. Cette valeur peut être une combinaison des indicateurs de bits [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) .

*Modifiées*<br/>
Pointeur vers un objet [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) . Les parties de ce descripteur de sécurité indiquées par le paramètre *si* sont appliquées au descripteur de sécurité de l’objet.

*GenericMapping*<br/>
Pointeur vers une structure [GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping) qui spécifie le mappage de chaque droit générique à des droits spécifiques pour l’objet.

*Lexical*<br/>
Référence à l’objet [caccesstoken,](../../atl/reference/caccesstoken-class.md) pour le processus client au nom duquel l’objet est créé.

*AutoInheritFlags*<br/>
Jeu d’indicateurs de bits qui contrôlent la façon dont les entrées de contrôle d’accès (ACE) sont héritées de *pParent*. Pour plus d’informations, consultez [CreatePrivateObjectSecurityEx](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) .

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true en cas de réussite, false en cas d'échec.

### <a name="remarks"></a>Notes

La deuxième méthode permet de spécifier le GUID du type d’objet de l’objet ou de contrôler la façon dont les ACE sont héritées.

## <a name="see-also"></a>Voir aussi

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc, classe](../../atl/reference/csecuritydesc-class.md)
