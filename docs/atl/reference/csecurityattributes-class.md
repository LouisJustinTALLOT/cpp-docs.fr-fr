---
title: Vue, classe
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: ebffbea120101a77450a5e8da3cdb6e34723e7be
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496501"
---
# <a name="csecurityattributes-class"></a>Vue, classe

Cette classe est un wrapper léger pour la structure des attributs de sécurité.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Vue:: vue](#csecurityattributes)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[Vue:: Set](#set)|Appelez cette méthode pour définir les attributs de l' `CSecurityAttributes` objet.|

## <a name="remarks"></a>Notes

La `SECURITY_ATTRIBUTES` structure contient un descripteur de [sécurité](/windows/win32/api/winnt/ns-winnt-security_descriptor) utilisé pour la création d’un objet et spécifie si le handle récupéré en spécifiant cette structure peut être hérité.

Pour obtenir une présentation du modèle de contrôle d’accès dans Windows, consultez [Access Control](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Configuration requise

**En-tête:** ATLSecurity. h

##  <a name="csecurityattributes"></a>  CSecurityAttributes::CSecurityAttributes

Constructeur.

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSecurityDescriptor*<br/>
Référence à un descripteur de sécurité.

*bInheritsHandle*<br/>
Spécifie si le handle retourné est hérité quand un nouveau processus est créé. Si ce membre a la valeur true, le nouveau processus hérite du handle.

##  <a name="set"></a>  CSecurityAttributes::Set

Appelez cette méthode pour définir les attributs de l' `CSecurityAttributes` objet.

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSecurityDescriptor*<br/>
Référence à un descripteur de sécurité.

*bInheritHandle*<br/>
Spécifie si le handle retourné est hérité quand un nouveau processus est créé. Si ce membre a la valeur true, le nouveau processus hérite du handle.

### <a name="remarks"></a>Notes

Cette méthode est utilisée par le constructeur pour initialiser l' `CSecurityAttributes` objet.

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[descripteur de sécurité](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
