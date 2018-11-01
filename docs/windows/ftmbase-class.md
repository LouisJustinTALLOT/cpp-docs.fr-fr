---
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
ms.openlocfilehash: fb7f103d8ea647f554d9bbf26c2e218d34f6b1ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431848"
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

Pour plus d’informations, consultez [runtimeclass, classe](runtimeclass-class.md).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

| Nom                         | Description                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase::FtmBase](#ftmbase) | Initialise une nouvelle instance de la classe `FtmBase`. |

### <a name="public-methods"></a>M&#233;thodes publiques

| Nom                                                               | Description                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase::CreateGlobalInterfaceTable](#createglobalinterfacetable) | Crée un tableau global d’interface (GIT).                                                                                                                              |
| [FtmBase::DisconnectObject](#disconnectobject)                     | Force libère toutes les connexions externes à un objet. Serveur de l’objet appelle l’implémentation de l’objet de cette méthode avant d’arrêter.                |
| [FtmBase::GetMarshalSizeMax](#getmarshalsizemax)                   | Obtenir la limite supérieure sur le nombre d’octets nécessaires pour marshaler le pointeur d’interface spécifié sur l’objet spécifié.                                                |
| [FtmBase::GetUnmarshalClass](#getunmarshalclass)                   | Obtient le CLSID COM utilise pour localiser la DLL contenant le code pour le proxy correspondant. COM charge cette DLL pour créer une instance non initialisée du proxy. |
| [FtmBase::MarshalInterface](#marshalinterface)                     | Écrit dans un flux les données requises pour initialiser l’objet proxy dans un processus client.                                                                          |
| [FtmBase::ReleaseMarshalData](#releasemarshaldata)                 | Détruit un paquet de données marshalé.                                                                                                                                    |
| [FtmBase::UnmarshalInterface](#unmarshalinterface)                 | Initialise un proxy nouvellement créé et retourne un pointeur d’interface au proxy.                                                                                    |

### <a name="public-data-members"></a>Membres de données publics

| Nom                                | Description                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase::marshaller_](#marshaller) | Contient une référence à FTM. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`FtmBase`

## <a name="requirements"></a>Configuration requise

**En-tête :** ftm.h

**Espace de noms :** Microsoft::WRL

## <a name="createglobalinterfacetable"></a>FtmBase::CreateGlobalInterfaceTable

Crée un tableau global d’interface (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Paramètres

*GIT*<br/>
Lorsque cette opération se termine, un pointeur vers un tableau global d’interface.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le `IGlobalInterfaceTable` rubrique dans le `COM Interfaces` sous-rubrique de la `COM Reference` rubrique dans MSDN Library.

## <a name="disconnectobject"></a>FtmBase::DisconnectObject

Force libère toutes les connexions externes à un objet. Serveur de l’objet appelle l’implémentation de l’objet de cette méthode avant d’arrêter.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé pour une future utilisation ; doit être nul.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="ftmbase"></a>FtmBase::FtmBase

Initialise une nouvelle instance de la classe `FtmBase`.

```cpp
FtmBase();
```

## <a name="getmarshalsizemax"></a>FtmBase::GetMarshalSizeMax

Obtenir la limite supérieure sur le nombre d’octets nécessaires pour marshaler le pointeur d’interface spécifié sur l’objet spécifié.

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
Référence à l’identificateur de l’interface doivent être marshalées.

*PV*<br/>
Pointeur d’interface doivent être marshalées ; peut être NULL.

*dwDestContext*<br/>
Contexte de destination où l’interface spécifiée doit être marshalé.

Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.

Actuellement, unmarshaling peut se produire dans un autre cloisonnement du processus en cours (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).

*pvDestContext*<br/>
Réservé pour une utilisation ultérieure ; doit être NULL.

*mshlflags*<br/>
Indicateur qui spécifie si les données doivent être marshalées doit être transmise au processus client, le cas par défaut, ou écrites dans une table globale, où il peut être extrait par plusieurs clients. Spécifiez une ou plusieurs valeurs d’énumération MSHLFLAGS.

*pSize*<br/>
Lorsque cette opération se termine, pointeur vers la limite supérieure de la quantité de données à écrire dans le flux de marshaling.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_FAIL ou E_NOINTERFACE.

## <a name="getunmarshalclass"></a>FtmBase::GetUnmarshalClass

Obtient le CLSID COM utilise pour localiser la DLL contenant le code pour le proxy correspondant. COM charge cette DLL pour créer une instance non initialisée du proxy.

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
Référence à l’identificateur de l’interface doivent être marshalées.

*PV*<br/>
Pointeur vers l’interface doivent être marshalées ; peut d’être NULL si l’appelant n’a pas un pointeur vers l’interface souhaitée.

*dwDestContext*<br/>
Contexte de destination où l’interface spécifiée doit être marshalé.

Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.

Unmarshaling peut se produire dans un autre cloisonnement du processus en cours (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).

*pvDestContext*<br/>
Réservé pour une utilisation ultérieure ; doit être NULL.

*mshlflags*<br/>
Lorsque cette opération se termine, pointeur vers le CLSID à utiliser pour créer un proxy dans le processus client.

*pCid*

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, S_FALSE.

## <a name="marshalinterface"></a>FtmBase::MarshalInterface

Écrit dans un flux les données requises pour initialiser l’objet proxy dans un processus client.

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
Référence à l’identificateur de l’interface doivent être marshalées. Cette interface doit être dérivée du `IUnknown` interface.

*PV*<br/>
Pointeur vers le pointeur d’interface doivent être marshalées ; peut d’être NULL si l’appelant n’a pas un pointeur vers l’interface souhaitée.

*dwDestContext*<br/>
Contexte de destination où l’interface spécifiée doit être marshalé.

Spécifiez une ou plusieurs valeurs d’énumération MSHCTX.

Unmarshaling peut se produire dans un autre cloisonnement du processus en cours (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus en cours (MSHCTX_LOCAL).

*pvDestContext*<br/>
Réservé pour une future utilisation ; doit être nul.

*mshlflags*<br/>
Spécifie si les données doivent être marshalées doit être transmise au processus client, le cas par défaut, ou écrites dans une table globale, où il peut être extrait par plusieurs clients.

### <a name="return-value"></a>Valeur de retour

S_OK le pointeur d’interface a été marshalé avec succès.

E_NOINTERFACE l’interface spécifiée n’est pas pris en charge.

STG_E_MEDIUMFULL le flux de données est plein.

E_FAIL l’opération a échoué.

## <a name="marshaller"></a>FtmBase::marshaller_

Contient une référence à FTM.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="releasemarshaldata"></a>FtmBase::ReleaseMarshalData

Détruit un paquet de données marshalé.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Paramètres

*pStm*<br/>
Pointeur vers un flux qui contient le paquet de données d’être détruit.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="unmarshalinterface"></a>FtmBase::UnmarshalInterface

Initialise un proxy nouvellement créé et retourne un pointeur d’interface au proxy.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Paramètres

*pStm*<br/>
Pointeur vers le flux à partir duquel le pointeur d’interface doit être marshalé.

*riid*<br/>
Référence à l’identificateur de l’interface pour être marshalé.

*PPV*<br/>
Lorsque cette opération se termine, l’adresse d’une variable pointeur qui reçoit le pointeur d’interface demandé dans *riid*. Si cette opération est réussie, **ppv* contient le pointeur d’interface requis de l’interface pour être marshalé.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_NOINTERFACE ou E_FAIL.
