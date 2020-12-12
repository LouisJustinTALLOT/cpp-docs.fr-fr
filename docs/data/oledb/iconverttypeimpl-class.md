---
description: 'En savoir plus sur : classe Iconverttypeimpl,'
title: IConvertTypeImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
ms.openlocfilehash: 5ac0e70432dbb81bd3f8aa30fd2adb9cb9e3fc30
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317560"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl, classe

Fournit une implémentation de l’interface [IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IConvertTypeImpl` .

## <a name="requirements"></a>Spécifications

**En-tête :** atldb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

| Nom | Description |
|-|-|
|[CanConvert](#canconvert)|Donne des informations sur la disponibilité des conversions de type sur une commande ou sur un ensemble de lignes.|

## <a name="remarks"></a>Notes

Cette interface est obligatoire sur les commandes, les ensembles de lignes et les ensembles de lignes d’index. `IConvertTypeImpl` implémente l’interface en déléguant à l’objet de conversion fourni par OLE DB.

## <a name="iconverttypeimplcanconvert"></a><a name="canconvert"></a> Iconverttypeimpl, :: CanConvert

Donne des informations sur la disponibilité des conversions de type sur une commande ou sur un ensemble de lignes.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>Paramètres

Consultez [IConvertType :: CanConvert](/previous-versions/windows/desktop/ms711224(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

### <a name="remarks"></a>Notes

Utilise OLE DB la conversion des données dans `MSADC.DLL` .

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
