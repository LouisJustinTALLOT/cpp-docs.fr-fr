---
title: Classe CSecurityAttributes
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: e0ac813008a028bb233adfb4c7409a0ad62a6b78
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746506"
---
# <a name="csecurityattributes-class"></a>Classe CSecurityAttributes

Cette classe est un emballage mince pour la structure des attributs de sécurité.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
|[CSecurityAttributes::Set](#set)|Appelez cette méthode pour définir `CSecurityAttributes` les attributs de l’objet.|

## <a name="remarks"></a>Notes

La `SECURITY_ATTRIBUTES` structure contient un [descripteur de sécurité](/windows/win32/api/winnt/ns-winnt-security_descriptor) utilisé pour la création d’un objet et précise si la poignée récupérée en spécifiant cette structure est héréditaire.

Pour une introduction au modèle de contrôle d’accès dans Windows, voir [Contrôle d’accès](/windows/win32/SecAuthZ/access-control) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>Spécifications

**En-tête:** atlsecurity.h

## <a name="csecurityattributescsecurityattributes"></a><a name="csecurityattributes"></a>CSecurityAttributes::CSecurityAttributes

Constructeur.

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSecurityDescriptor (en anglais)*<br/>
Référence à un descripteur de sécurité.

*bInheritsHandle*<br/>
Spécifie si le handle retourné est hérité quand un nouveau processus est créé. Si ce membre a la valeur true, le nouveau processus hérite du handle.

## <a name="csecurityattributesset"></a><a name="set"></a>CSecurityAttributes::Set

Appelez cette méthode pour définir `CSecurityAttributes` les attributs de l’objet.

```cpp
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>Paramètres

*rSecurityDescriptor (en anglais)*<br/>
Référence à un descripteur de sécurité.

*bInheritHandle*<br/>
Spécifie si le handle retourné est hérité quand un nouveau processus est créé. Si ce membre a la valeur true, le nouveau processus hérite du handle.

### <a name="remarks"></a>Notes

Cette méthode est utilisée par le `CSecurityAttributes` constructeur pour initialiser l’objet.

## <a name="see-also"></a>Voir aussi

[Échantillon de sécurité](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[descripteur de sécurité](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Fonctions globales de sécurité](../../atl/reference/security-global-functions.md)
