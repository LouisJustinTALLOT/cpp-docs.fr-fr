---
description: 'En savoir plus sur : classe FtmBase'
title: FtmBase (classe)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
- ftm/Microsoft::WRL::FtmBaseCreateGlobalInterfaceTable
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
- ftm/Microsoft::WRL::FtmBase::FtmBase
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
- ftm/Microsoft::WRL::FtmBase::marshaller_
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
helpviewer_keywords:
- Microsoft::WRL::FtmBase class
- Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable method
- Microsoft::WRL::FtmBase::DisconnectObject method
- Microsoft::WRL::FtmBase::FtmBase, constructor
- Microsoft::WRL::FtmBase::GetMarshalSizeMax method
- Microsoft::WRL::FtmBase::GetUnmarshalClass method
- Microsoft::WRL::FtmBase::MarshalInterface method
- Microsoft::WRL::FtmBase::marshaller_ data member
- Microsoft::WRL::FtmBase::ReleaseMarshalData method
- Microsoft::WRL::FtmBase::UnmarshalInterface method
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
ms.openlocfilehash: dc7ae3768233dd51d34b48da8c12a2d4b6bed773
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250086"
---
# <a name="ftmbase-class"></a>FtmBase (classe)

Représente un objet marshaler libre de threads.

## <a name="syntax"></a>Syntaxe

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [RuntimeClass, classe](runtimeclass-class.md).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

| Nom                         | Description                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase :: FtmBase](#ftmbase) | Initialise une nouvelle instance de la classe `FtmBase`. |

### <a name="public-methods"></a>M&#233;thodes publiques

| Nom                                                               | Description                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase :: Createglobalinterfacetable,](#createglobalinterfacetable) | Crée une table d’interface globale (GIT).                                                                                                                              |
| [FtmBase ::D isconnectObject](#disconnectobject)                     | Libère toutes les connexions externes à un objet de force. Le serveur de l’objet appelle l’implémentation de cette méthode de l’objet avant de s’arrêter.                |
| [FtmBase :: GetMarshalSizeMax](#getmarshalsizemax)                   | Obtient la limite supérieure du nombre d’octets nécessaires pour marshaler le pointeur d’interface spécifié sur l’objet spécifié.                                                |
| [FtmBase :: GetUnmarshalClass](#getunmarshalclass)                   | Obtient le CLSID utilisé par COM pour localiser la DLL contenant le code pour le proxy correspondant. COM charge cette DLL pour créer une instance non initialisée du proxy. |
| [FtmBase :: MarshalInterface](#marshalinterface)                     | Écrit dans un flux les données requises pour initialiser un objet proxy dans un processus client.                                                                          |
| [FtmBase :: ReleaseMarshalData,](#releasemarshaldata)                 | Détruit un paquet de données marshalé.                                                                                                                                    |
| [FtmBase :: UnmarshalInterface](#unmarshalinterface)                 | Initialise un proxy nouvellement créé et retourne un pointeur d’interface vers ce proxy.                                                                                    |

### <a name="public-data-members"></a>Membres de données publics

| Nom                                | Description                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase :: marshaller_](#marshaller) | Contient une référence au marshaleur libre de threads. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`FtmBase`

## <a name="requirements"></a>Spécifications

**En-tête :** FTM. h

**Espace de noms :** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a> FtmBase :: Createglobalinterfacetable,

Crée une table d’interface globale (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Paramètres

*git*<br/>
Lorsque cette opération est terminée, il s’agit d’un pointeur vers une table d’interface globale.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [`IGlobalInterfaceTable`](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable).

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a> FtmBase ::D isconnectObject

Libère toutes les connexions externes à un objet de force. Le serveur de l’objet appelle l’implémentation de cette méthode de l’objet avant de s’arrêter.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé pour une future utilisation ; doit être nul.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a> FtmBase :: FtmBase

Initialise une nouvelle instance de la classe `FtmBase`.

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a> FtmBase :: GetMarshalSizeMax

Obtient la limite supérieure du nombre d’octets nécessaires pour marshaler le pointeur d’interface spécifié sur l’objet spécifié.

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
Référence à l’identificateur de l’interface à marshaler.

*va*<br/>
Pointeur d’interface à marshaler ; peut avoir la valeur NULL.

*dwDestContext*<br/>
Contexte de destination dans lequel l’interface spécifiée doit être démarshalée.

Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.

Actuellement, le démarshaling peut se produire dans un autre cloisonnement du processus en cours (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).

*pvDestContext*<br/>
Réservé à une utilisation ultérieure ; doit avoir la valeur NULL.

*mshlflags*<br/>
Indicateur précisant si les données à marshaler doivent être retransmises au processus client (cas typique) ou écrites dans une table globale, où elles peuvent être récupérées par plusieurs clients. Spécifiez une ou plusieurs valeurs d’énumération MSHLFLAGS.

*pSize*<br/>
Lorsque cette opération est terminée, pointeur vers la limite supérieure de la quantité de données à écrire dans le flux de marshaling.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, E_FAIL ou E_NOINTERFACE.

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a> FtmBase :: GetUnmarshalClass

Obtient le CLSID utilisé par COM pour localiser la DLL contenant le code pour le proxy correspondant. COM charge cette DLL pour créer une instance non initialisée du proxy.

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>Paramètres

*riid*<br/>
Référence à l’identificateur de l’interface à marshaler.

*va*<br/>
Pointeur vers l’interface à marshaler ; peut avoir la valeur NULL si l’appelant n’a pas de pointeur vers l’interface souhaitée.

*dwDestContext*<br/>
Contexte de destination dans lequel l’interface spécifiée doit être démarshalée.

Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.

Le démarshaling peut se produire dans un autre cloisonnement du processus en cours (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).

*pvDestContext*<br/>
Réservé à une utilisation ultérieure ; doit avoir la valeur NULL.

*mshlflags*<br/>
Lorsque cette opération est terminée, pointeur vers le CLSID à utiliser pour créer un proxy dans le processus client.

*pCid*

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, S_FALSE.

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a> FtmBase :: MarshalInterface

Écrit dans un flux les données requises pour initialiser un objet proxy dans un processus client.

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>Paramètres

*pStm*<br/>
Pointeur vers le flux à utiliser pendant le marshaling.

*riid*<br/>
Référence à l’identificateur de l’interface à marshaler. Cette interface doit être dérivée de l'interface `IUnknown` .

*va*<br/>
Pointeur vers le pointeur d’interface à marshaler ; peut avoir la valeur NULL si l’appelant n’a pas de pointeur vers l’interface souhaitée.

*dwDestContext*<br/>
Contexte de destination dans lequel l’interface spécifiée doit être démarshalée.

Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.

Le démarshaling peut se produire dans un autre cloisonnement du processus en cours (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).

*pvDestContext*<br/>
Réservé pour une future utilisation ; doit être nul.

*mshlflags*<br/>
Spécifie si les données à marshaler doivent être retransmises au processus client (cas typique) ou écrites dans une table globale, où elles peuvent être récupérées par plusieurs clients.

### <a name="return-value"></a>Valeur renvoyée

S_OK le pointeur d’interface a été marshalé avec succès.

E_NOINTERFACE l’interface spécifiée n’est pas prise en charge.

STG_E_MEDIUMFULL le flux est plein.

E_FAIL l’opération a échoué.

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a> FtmBase :: marshaller_

Contient une référence au marshaleur libre de threads.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a> FtmBase :: ReleaseMarshalData,

Détruit un paquet de données marshalé.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Paramètres

*pStm*<br/>
Pointeur vers un flux qui contient le paquet de données à détruire.

### <a name="return-value"></a>Valeur renvoyée

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a> FtmBase :: UnmarshalInterface

Initialise un proxy nouvellement créé et retourne un pointeur d’interface vers ce proxy.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Paramètres

*pStm*<br/>
Pointeur vers le flux à partir duquel le pointeur d’interface doit être démarshalé.

*riid*<br/>
Référence à l’identificateur de l’interface à démarshaler.

*ppv*<br/>
Lorsque cette opération est terminée, il s’agit de l’adresse d’une variable pointeur qui reçoit le pointeur d’interface demandé dans *riid*. Si cette opération réussit, **PPV* contient le pointeur d’interface demandé de l’interface à démarshaler.

### <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, E_NOINTERFACE ou E_FAIL.
