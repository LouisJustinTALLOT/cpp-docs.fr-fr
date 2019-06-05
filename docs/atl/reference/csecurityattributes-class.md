---
title: CSecurityAttributes, classe
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: b26de7a2a3426ed2fe86bd7ef50f6c5410fa5364
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503194"
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes, classe

Cette classe est un simple wrapper pour la structure d’attributs de sécurité.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSecurityAttributes::CSecurityAttributes](#csecurityattributes)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSecurityAttributes::Set](#set)|Appelez cette méthode pour définir les attributs de la `CSecurityAttributes` objet.|

## <a name="remarks"></a>Notes

Le `SECURITY_ATTRIBUTES` structure contient un [descripteur de sécurité](/windows/desktop/api/winnt/ns-winnt-_security_descriptor) utilisée pour la création d’un objet et spécifie si le handle extrait en spécifiant cette structure peut être hérité.

Pour une présentation du modèle de contrôle d’accès dans Windows, consultez [contrôle d’accès](/windows/desktop/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlsecurity.h

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

Appelez cette méthode pour définir les attributs de la `CSecurityAttributes` objet.

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSecurityDescriptor*<br/>
Référence à un descripteur de sécurité.

*bInheritHandle*<br/>
Spécifie si le handle retourné est hérité quand un nouveau processus est créé. Si ce membre a la valeur true, le nouveau processus hérite du handle.

### <a name="remarks"></a>Notes

Cette méthode est utilisée par le constructeur pour initialiser le `CSecurityAttributes` objet.

## <a name="see-also"></a>Voir aussi

[Exemple de sécurité](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[descripteur de sécurité](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
