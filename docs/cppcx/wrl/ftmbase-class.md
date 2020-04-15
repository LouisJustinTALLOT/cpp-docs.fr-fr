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
ms.openlocfilehash: d37cdddda8cf8894016ed80b9055fe106b1600f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371512"
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

Pour plus d’informations, voir [RuntimeClass Class](runtimeclass-class.md).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

| Nom                         | Description                                        |
| ---------------------------- | -------------------------------------------------- |
| [Base Ftm::FtmBase](#ftmbase) | Initialise une nouvelle instance de la classe `FtmBase`. |

### <a name="public-methods"></a>M&#233;thodes publiques

| Nom                                                               | Description                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase::CreateGlobalInterfaceTable](#createglobalinterfacetable) | Crée une table d’interface globale (GIT).                                                                                                                              |
| [FtmBase::DestconnectObject](#disconnectobject)                     | Libère de force toutes les connexions externes à un objet. Le serveur de l’objet appelle la mise en œuvre de cette méthode avant l’arrêt de cette méthode.                |
| [FtmBase::GetMarshalSizeMax](#getmarshalsizemax)                   | Obtenez la limite supérieure sur le nombre d’octets nécessaires pour mobiliser le pointeur d’interface spécifié sur l’objet spécifié.                                                |
| [FtmBase::GetUnmarshalClass](#getunmarshalclass)                   | Obtient le CLSID que COM utilise pour localiser le DLL contenant le code pour le proxy correspondant. COM charge ce DLL pour créer un exemple uninitialisé de la procuration. |
| [Base Ftm::MarshalInterface](#marshalinterface)                     | Écrit dans un flux les données nécessaires pour initialiser un objet proxy dans un processus client.                                                                          |
| [FtmBase::ReleaseMarshalData](#releasemarshaldata)                 | Détruit un paquet de données marshaled.                                                                                                                                    |
| [Base Ftm::UnmarshalInterface](#unmarshalinterface)                 | Initialise un proxy nouvellement créé et renvoie un pointeur d’interface à ce proxy.                                                                                    |

### <a name="public-data-members"></a>Membres de données publics

| Nom                                | Description                                       |
| ----------------------------------- | ------------------------------------------------- |
| [Base Ftm::marshaller_](#marshaller) | Tient une référence au maréchal libre fileté. |

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`FtmBase`

## <a name="requirements"></a>Spécifications

**En-tête:** ftm.h

**Espace de noms :** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a>FtmBase::CreateGlobalInterfaceTable

Crée une table d’interface globale (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Paramètres

*Git*<br/>
Lorsque cette opération se termine, un pointeur vers une table d’interface globale.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir le `IGlobalInterfaceTable` sujet dans le `COM Interfaces` sous- haut-plan du `COM Reference` sujet dans la Bibliothèque MSDN.

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a>FtmBase::DestconnectObject

Libère de force toutes les connexions externes à un objet. Le serveur de l’objet appelle la mise en œuvre de cette méthode avant l’arrêt de cette méthode.

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

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a>Base Ftm::FtmBase

Initialise une nouvelle instance de la classe `FtmBase`.

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a>FtmBase::GetMarshalSizeMax

Obtenez la limite supérieure sur le nombre d’octets nécessaires pour mobiliser le pointeur d’interface spécifié sur l’objet spécifié.

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
Référence à l’identifiant de l’interface à mobiliser.

*Pv*<br/>
Pointeur d’interface à marshaled ; peut être NULL.

*dwDestContexte*<br/>
Contexte de destination où l’interface spécifiée doit être non-ramshalée.

Spécifier une ou plusieurs valeurs d’énumération MSHCTX.

À l’heure actuelle, le non-mariage peut se produire soit dans un autre appartement du processus actuel (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus actuel (MSHCTX_LOCAL).

*pvDestContexte*<br/>
Réservé à une utilisation future; doit être NULL.

*mshlflags mshlflags*<br/>
Le drapeau indiquant si les données à rassembler doivent être transmises au processus client — le cas type — ou écrites à une table globale, où elles peuvent être récupérées par plusieurs clients. Spécifier une ou plusieurs valeurs d’énumération MSHLFLAGS.

*Psize*<br/>
Lorsque cette opération se termine, indiquez à la limite supérieure la quantité de données à écrire au flux de marshaling.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, E_FAIL ou E_NOINTERFACE.

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a>FtmBase::GetUnmarshalClass

Obtient le CLSID que COM utilise pour localiser le DLL contenant le code pour le proxy correspondant. COM charge ce DLL pour créer un exemple uninitialisé de la procuration.

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
Référence à l’identifiant de l’interface à mobiliser.

*Pv*<br/>
Pointeur à l’interface à mobiliser; peut être NULL si l’appelant n’a pas un pointeur à l’interface désirée.

*dwDestContexte*<br/>
Contexte de destination où l’interface spécifiée doit être non-ramshalée.

Spécifier une ou plusieurs valeurs d’énumération MSHCTX.

Unmarshaling peut se produire soit dans un autre appartement du processus actuel (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus actuel (MSHCTX_LOCAL).

*pvDestContexte*<br/>
Réservé à une utilisation future; doit être NULL.

*mshlflags mshlflags*<br/>
Lorsque cette opération se termine, indiquez au CLSID d’être utilisé pour créer un proxy dans le processus client.

*pCid*

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, S_FALSE.

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a>Base Ftm::MarshalInterface

Écrit dans un flux les données nécessaires pour initialiser un objet proxy dans un processus client.

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

*pStm (pStm)*<br/>
Pointeur sur le flux à utiliser pendant le marshaling.

*riid*<br/>
Référence à l’identifiant de l’interface à mobiliser. Cette interface doit être dérivée de l'interface `IUnknown` .

*Pv*<br/>
Pointeur sur le pointeur d’interface à être marshaled; peut être NULL si l’appelant n’a pas un pointeur à l’interface désirée.

*dwDestContexte*<br/>
Contexte de destination où l’interface spécifiée doit être non-ramshalée.

Spécifier une ou plusieurs valeurs d’énumération MSHCTX.

Unmarshaling peut se produire dans un autre appartement du processus actuel (MSHCTX_INPROC) ou dans un autre processus sur le même ordinateur que le processus actuel (MSHCTX_LOCAL).

*pvDestContexte*<br/>
Réservé pour une future utilisation ; doit être nul.

*mshlflags mshlflags*<br/>
Précise si les données à rassembler doivent être transmises au processus client — le cas type — ou écrites à une table globale, où elles peuvent être récupérées par plusieurs clients.

### <a name="return-value"></a>Valeur de retour

S_OK Le pointeur d’interface a été mobilisé avec succès.

E_NOINTERFACE L’interface spécifiée n’est pas prise en charge.

STG_E_MEDIUMFULL Le flux est plein.

E_FAIL L’opération a échoué.

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a>Base Ftm::marshaller_

Tient une référence au maréchal libre fileté.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a>FtmBase::ReleaseMarshalData

Détruit un paquet de données marshaled.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Paramètres

*pStm (pStm)*<br/>
Pointeur vers un flux qui contient le paquet de données à détruire.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a>Base Ftm::UnmarshalInterface

Initialise un proxy nouvellement créé et renvoie un pointeur d’interface à ce proxy.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Paramètres

*pStm (pStm)*<br/>
Pointeur vers le flux à partir duquel le pointeur d’interface doit être non-ramshaled.

*riid*<br/>
Référence à l’identifiant de l’interface à délimiter.

*Ppv*<br/>
Lorsque cette opération se termine, l’adresse d’une variable de pointeur qui reçoit le pointeur d’interface demandé en *riid*. Si cette opération est réussie,*ppv* contient le pointeur d’interface demandé de l’interface à démarshaler.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de succès; autrement, E_NOINTERFACE ou E_FAIL.
