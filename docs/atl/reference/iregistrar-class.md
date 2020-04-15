---
title: IRegistrar Interface
ms.date: 02/01/2017
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
ms.openlocfilehash: 98943fe294322715723bd91207a6f3320ca1ffb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329463"
---
# <a name="iregistrar-interface"></a>IRegistrar Interface

Cette interface est définie dans atliface.h et est utilisée en interne par les fonctions membres de CAtlModule telles que [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).

## <a name="syntax"></a>Syntaxe

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>Notes

Consultez le sujet [à l’aide de paramètres remplaçables (préprocesseur du registraire)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) pour plus de détails.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Enregistre la ressource. |
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Désenregistrer la ressource.|
|[IRegistrar::FileRegister](#fileregister)|Enregistre le fichier.|
|[IRegistrar::FileUnregister](#fileunregister)|Désenregistrer le fichier.|
|[IRegistrar::StringRegister](#stringregister)|Enregistre la chaîne.|
|[IRegistrar::StringUnregister](#stringunregister)|Déchaîne la chaîne|
|[IRegistrar::ResourceRegister](#resourceregister)|Enregistre la ressource.|
|[IRegistrar::ResourceUnregister](#resourceunregister)|Désenregistrer la ressource.|

## <a name="requirements"></a>Spécifications

**En-tête:** atlifase.h

## <a name="iregistrarresourceregistersz"></a><a name="resourceregistersz"></a>IRegistrar::ResourceRegisterSz

Enregistre la ressource.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregistersz"></a><a name="resourceunregistersz"></a>IRegistrar::ResourceUnregisterSz

Désenregistrer la ressource.

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarfileregister"></a><a name="fileregister"></a>IRegistrar::FileRegister

Enregistre le fichier.

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarfileunregister"></a><a name="fileunregister"></a>IRegistrar::FileUnregister

Désenregistrer le fichier.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarstringregister"></a><a name="stringregister"></a>IRegistrar::StringRegister

Enregistre les données de chaîne spécifiées.

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarstringunregister"></a><a name="stringunregister"></a>IRegistrar::StringUnregister

Non inscrit les données de chaîne spécifiées.

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarresourceregister"></a><a name="resourceregister"></a>IRegistrar::ResourceRegister

Enregistre la ressource.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregister"></a><a name="resourceunregister"></a>IRegistrar::ResourceUnregister

Désenregistrer la ressource.

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>Voir aussi

[Utilisation de paramètres remplaçables (Préprocesseur du registraire)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de modules](../../atl/atl-module-classes.md)<br/>
[Composant du Registre (enregistreur)](../../atl/atl-registry-component-registrar.md)
