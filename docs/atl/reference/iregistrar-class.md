---
description: 'En savoir plus sur : interface IRegistrar'
title: Interface IRegistrar
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
ms.openlocfilehash: 9a138468ccbf21594c4e9d88d1ed2387a4c1052a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139163"
---
# <a name="iregistrar-interface"></a>Interface IRegistrar

Cette interface est définie dans atliface. h et est utilisée en interne par les fonctions membres CAtlModule telles que [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).

## <a name="syntax"></a>Syntaxe

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez la rubrique [utilisation de paramètres remplaçables (le préprocesseur du Bureau d’enregistrement)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) .

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IRegistrar :: ResourceRegisterSz](#resourceregistersz)|Inscrit la ressource. |
|[IRegistrar :: ResourceUnregisterSz](#resourceunregistersz)| Annule l’inscription de la ressource.|
|[IRegistrar :: FileRegister](#fileregister)|Inscrit le fichier.|
|[IRegistrar :: FileUnregister](#fileunregister)|Annule l’inscription du fichier.|
|[IRegistrar :: StringRegister](#stringregister)|Inscrit la chaîne.|
|[IRegistrar :: StringUnregister](#stringunregister)|Annule l’inscription de la chaîne|
|[IRegistrar :: ResourceRegister](#resourceregister)|Inscrit la ressource.|
|[IRegistrar :: ResourceUnregister](#resourceunregister)|Annule l’inscription de la ressource.|

## <a name="requirements"></a>Spécifications

**En-tête :** atlifase. h

## <a name="iregistrarresourceregistersz"></a><a name="resourceregistersz"></a> IRegistrar :: ResourceRegisterSz

Inscrit la ressource.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregistersz"></a><a name="resourceunregistersz"></a> IRegistrar :: ResourceUnregisterSz

Annule l’inscription de la ressource.

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarfileregister"></a><a name="fileregister"></a> IRegistrar :: FileRegister

Inscrit le fichier.

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarfileunregister"></a><a name="fileunregister"></a> IRegistrar :: FileUnregister

Annule l’inscription du fichier.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarstringregister"></a><a name="stringregister"></a> IRegistrar :: StringRegister

Inscrit les données de chaîne spécifiées.

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarstringunregister"></a><a name="stringunregister"></a> IRegistrar :: StringUnregister

Annule l’enregistrement des données de chaîne spécifiées.

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarresourceregister"></a><a name="resourceregister"></a> IRegistrar :: ResourceRegister

Inscrit la ressource.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregister"></a><a name="resourceunregister"></a> IRegistrar :: ResourceUnregister

Annule l’inscription de la ressource.

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>Voir aussi

[Utilisation de paramètres remplaçables (le préprocesseur du Bureau d’enregistrement)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)<br/>
[Composant du Registre (enregistreur)](../../atl/atl-registry-component-registrar.md)
