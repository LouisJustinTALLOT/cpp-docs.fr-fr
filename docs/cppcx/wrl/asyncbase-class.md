---
title: AsyncBase (classe)
ms.date: 10/08/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
- async/Microsoft::WRL::AsyncBase::AsyncBase
- async/Microsoft::WRL::AsyncBase::Cancel
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
- async/Microsoft::WRL::AsyncBase::Close
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
- async/Microsoft::WRL::AsyncBase::CurrentStatus
- async/Microsoft::WRL::AsyncBase::ErrorCode
- async/Microsoft::WRL::AsyncBase::FireCompletion
- async/Microsoft::WRL::AsyncBase::FireProgress
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
- async/Microsoft::WRL::AsyncBase::get_Id
- async/Microsoft::WRL::AsyncBase::get_Status
- async/Microsoft::WRL::AsyncBase::GetOnComplete
- async/Microsoft::WRL::AsyncBase::GetOnProgress
- async/Microsoft::WRL::AsyncBase::OnCancel
- async/Microsoft::WRL::AsyncBase::OnClose
- async/Microsoft::WRL::AsyncBase::OnStart
- async/Microsoft::WRL::AsyncBase::put_Id
- async/Microsoft::WRL::AsyncBase::PutOnComplete
- async/Microsoft::WRL::AsyncBase::PutOnProgress
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
helpviewer_keywords:
- Microsoft::WRL::AsyncBase class
- Microsoft::WRL::AsyncBase::AsyncBase, constructor
- Microsoft::WRL::AsyncBase::Cancel method
- Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall method
- Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall method
- Microsoft::WRL::AsyncBase::Close method
- Microsoft::WRL::AsyncBase::ContinueAsyncOperation method
- Microsoft::WRL::AsyncBase::CurrentStatus method
- Microsoft::WRL::AsyncBase::ErrorCode method
- Microsoft::WRL::AsyncBase::FireCompletion method
- Microsoft::WRL::AsyncBase::FireProgress method
- Microsoft::WRL::AsyncBase::get_ErrorCode method
- Microsoft::WRL::AsyncBase::get_Id method
- Microsoft::WRL::AsyncBase::get_Status method
- Microsoft::WRL::AsyncBase::GetOnComplete method
- Microsoft::WRL::AsyncBase::GetOnProgress method
- Microsoft::WRL::AsyncBase::OnCancel method
- Microsoft::WRL::AsyncBase::OnClose method
- Microsoft::WRL::AsyncBase::OnStart method
- Microsoft::WRL::AsyncBase::put_Id method
- Microsoft::WRL::AsyncBase::PutOnComplete method
- Microsoft::WRL::AsyncBase::PutOnProgress method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
ms.openlocfilehash: 8684096e76c08456a9c6813b7f04d79b820e41e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211552"
---
# <a name="asyncbase-class"></a>AsyncBase (classe)

Implémente la machine d'état asynchrone du Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename TComplete,
    typename TProgress = Details::Nil,
    AsyncResultType resultType = SingleResult
>
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;

template <typename TComplete, AsyncResultType resultType>
class AsyncBase<TComplete, Details::Nil, resultType> :
    public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>Paramètres

*TComplete*<br/>
Gestionnaire d’événements appelé lorsqu’une opération asynchrone se termine.

*TProgress*<br/>
Gestionnaire d’événements appelé lorsqu’une opération asynchrone en cours d’exécution signale la progression actuelle de l’opération.

*resultType*<br/>
L’une des valeurs d’énumération [asyncresulttype,](asyncresulttype-enumeration.md) . Par défaut, `SingleResult`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                               | Description
---------------------------------- | -------------------------------------------------
[AsyncBase :: AsyncBase](#asyncbase) | Initialise une instance de la classe `AsyncBase`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                         | Description
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase :: Cancel](#cancel)                 | Annule une opération asynchrone.
[AsyncBase :: Close](#close)                   | Ferme l’opération asynchrone.
[AsyncBase :: Firecompletion,](#firecompletion) | Appelle le gestionnaire d’événements de saisie semi-automatique, ou réinitialise le délégué de progression interne.
[AsyncBase :: FireProgress,](#fireprogress)     | Appelle le gestionnaire d’événements de progression actuel.
[AsyncBase :: get_ErrorCode](#get-errorcode)   | Récupère le code d’erreur pour l’opération asynchrone actuelle.
[AsyncBase :: get_Id](#get-id)                 | Récupère le handle de l’opération asynchrone.
[AsyncBase :: get_Status](#get-status)         | Récupère une valeur qui indique l’état de l’opération asynchrone.
[AsyncBase :: Getoncomplete,](#getoncomplete)   | Copie l’adresse du gestionnaire d’événements de saisie semi-automatique en cours dans la variable spécifiée.
[AsyncBase :: Getonprogress,](#getonprogress)   | Copie l’adresse du gestionnaire d’événements de progression actuel vers la variable spécifiée.
[AsyncBase ::p ut_Id](#put-id)                 | Définit le handle de l’opération asynchrone.
[AsyncBase ::P utOnComplete](#putoncomplete)   | Affecte la valeur spécifiée à l’adresse du gestionnaire d’événements de saisie semi-automatique.
[AsyncBase ::P utOnProgress](#putonprogress)   | Affecte la valeur spécifiée à l’adresse du gestionnaire d’événements de progression.

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                                         | Description
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase :: Checkvalidstatefordelegatecall,](#checkvalidstatefordelegatecall) | Teste si les propriétés de délégué peuvent être modifiées dans l’état asynchrone actuel.
[AsyncBase :: Checkvalidstateforresultscall,](#checkvalidstateforresultscall)   | Teste si les résultats d’une opération asynchrone peuvent être collectés dans l’état asynchrone actuel.
[AsyncBase :: Continueasyncoperation,](#continueasyncoperation)                 | Détermine si l’opération asynchrone doit continuer le traitement ou s’arrêter.
[AsyncBase :: currentStatus,](#currentstatus)                                   | Récupère l’état de l’opération asynchrone actuelle.
[AsyncBase :: ErrorCode](#errorcode)                                           | Récupère le code d’erreur pour l’opération asynchrone actuelle.
[AsyncBase :: OnCancel](#oncancel)                                             | En cas de substitution dans une classe dérivée, annule une opération asynchrone.
[AsyncBase :: OnClose](#onclose)                                               | En cas de substitution dans une classe dérivée, ferme une opération asynchrone.
[AsyncBase :: OnStart](#onstart)                                               | En cas de substitution dans une classe dérivée, démarre une opération asynchrone.
[AsyncBase :: Start](#start)                                                   | Démarre l’opération asynchrone.
[AsyncBase :: Trytransitiontocompleted,](#trytransitiontocompleted)             | Indique si l’opération asynchrone en cours est terminée.
[AsyncBase :: Trytransitiontoerror,](#trytransitiontoerror)                     | Indique si le code d’erreur spécifié peut modifier l’état d’erreur interne.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Spécifications

**En-tête :** Async. h

**Espace de noms :** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>AsyncBase :: AsyncBase

Initialise une instance de la classe `AsyncBase`.

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>AsyncBase :: Cancel

Annule une opération asynchrone.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Valeur de retour

Par défaut, retourne toujours S_OK.

### <a name="remarks"></a>Notes

`Cancel()`est une implémentation par défaut de `IAsyncInfo::Cancel` et ne fait pas de travail réel. Pour annuler réellement une opération asynchrone, substituez la `OnCancel()` méthode virtuelle pure.

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>AsyncBase :: Checkvalidstatefordelegatecall,

Teste si les propriétés de délégué peuvent être modifiées dans l’état asynchrone actuel.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Valeur de retour

S_OK si les propriétés de délégué peuvent être modifiées ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>AsyncBase :: Checkvalidstateforresultscall,

Teste si les résultats d’une opération asynchrone peuvent être collectés dans l’état asynchrone actuel.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Valeur de retour

S_OK si les résultats peuvent être collectés ; Sinon, E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseclose"></a><a name="close"></a>AsyncBase :: Close

Ferme l’opération asynchrone.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Valeur de retour

S_OK si l’opération se ferme ou est déjà fermée ; Sinon, E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Notes

`Close()`est une implémentation par défaut de `IAsyncInfo::Close` et ne fait pas de travail réel. Pour fermer réellement une opération asynchrone, substituez la `OnClose()` méthode virtuelle pure.

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>AsyncBase :: Continueasyncoperation,

Détermine si l’opération asynchrone doit continuer le traitement ou s’arrêter.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si l’état actuel de l’opération asynchrone est *démarré*, ce qui signifie que l’opération doit se poursuivre. Sinon, **`false`** , ce qui signifie que l’opération doit s’arrêter.

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>AsyncBase :: currentStatus,

Récupère l’état de l’opération asynchrone actuelle.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Paramètres

*statut*<br/>
Emplacement où cette opération stocke l’état actuel.

### <a name="remarks"></a>Notes

Cette opération est thread-safe.

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>AsyncBase :: ErrorCode

Récupère le code d’erreur pour l’opération asynchrone actuelle.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Paramètres

*error*<br/>
Emplacement où cette opération stocke le code d’erreur actuel.

### <a name="remarks"></a>Notes

Cette opération est thread-safe.

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>AsyncBase :: Firecompletion,

Appelle le gestionnaire d’événements de saisie semi-automatique, ou réinitialise le délégué de progression interne.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Notes

La première version de `FireCompletion()` réinitialise la variable de délégué de progression interne. La deuxième version appelle le gestionnaire d’événements d’achèvement si l’opération asynchrone est terminée.

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>AsyncBase :: FireProgress,

Appelle le gestionnaire d’événements de progression actuel.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Paramètres

*donnée*<br/>
Méthode de gestionnaire d’événements à appeler.

### <a name="remarks"></a>Notes

`ProgressTraits`est dérivé de la [structure ArgTraitsHelper](argtraitshelper-structure.md).

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>AsyncBase :: get_ErrorCode

Récupère le code d’erreur pour l’opération asynchrone actuelle.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Paramètres

*errorCode*<br/>
Emplacement où le code d’erreur actuel est stocké.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL si l’opération asynchrone en cours est fermée.

## <a name="asyncbaseget_id"></a><a name="get-id"></a>AsyncBase :: get_Id

Récupère le handle de l’opération asynchrone.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Paramètres

*id*<br/>
Emplacement où le descripteur doit être stocké.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Notes

Cette méthode implémente `IAsyncInfo::get_Id`.

## <a name="asyncbaseget_status"></a><a name="get-status"></a>AsyncBase :: get_Status

Récupère une valeur qui indique l’état de l’opération asynchrone.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Paramètres

*statut*<br/>
Emplacement où l’État doit être stocké. Pour plus d’informations, consultez `Windows::Foundation::AsyncStatus` énumération.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Notes

Cette méthode implémente `IAsyncInfo::get_Status`.

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>AsyncBase :: Getoncomplete,

Copie l’adresse du gestionnaire d’événements de saisie semi-automatique en cours dans la variable spécifiée.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Paramètres

*completeHandler*<br/>
Emplacement où est stockée l’adresse du gestionnaire d’événements de saisie semi-automatique en cours.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>AsyncBase :: Getonprogress,

Copie l’adresse du gestionnaire d’événements de progression actuel vers la variable spécifiée.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Paramètres

*progressHandler*<br/>
Emplacement où l’adresse du gestionnaire d’événements de progression actuel est stockée.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>AsyncBase :: OnCancel

En cas de substitution dans une classe dérivée, annule une opération asynchrone.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>AsyncBase :: OnClose

En cas de substitution dans une classe dérivée, ferme une opération asynchrone.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>AsyncBase :: OnStart

En cas de substitution dans une classe dérivée, démarre une opération asynchrone.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>AsyncBase ::p ut_Id

Définit le handle de l’opération asynchrone.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Paramètres

*id*<br/>
Handle différent de zéro.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_INVALIDARG ou E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>AsyncBase ::P utOnComplete

Affecte la valeur spécifiée à l’adresse du gestionnaire d’événements de saisie semi-automatique.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Paramètres

*completeHandler*<br/>
Adresse à laquelle le gestionnaire d’événements de saisie semi-automatique est défini.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>AsyncBase ::P utOnProgress

Affecte la valeur spécifiée à l’adresse du gestionnaire d’événements de progression.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Paramètres

*progressHandler*<br/>
Adresse à laquelle le gestionnaire d’événements Progress est défini.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasestart"></a><a name="start"></a>AsyncBase :: Start

Démarre l’opération asynchrone.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Valeur de retour

S_OK si l’opération démarre ou est déjà démarrée ; Sinon, E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Notes

`Start()`est une méthode protégée qui n’est pas visible de l’extérieur, car les opérations asynchrones démarrent à chaud avant de retourner à l’appelant.

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>AsyncBase :: Trytransitiontocompleted,

Indique si l’opération asynchrone en cours est terminée.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si l’opération asynchrone est terminée ; Sinon, **`false`** .

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>AsyncBase :: Trytransitiontoerror,

Indique si le code d’erreur spécifié peut modifier l’état d’erreur interne.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Paramètres

*error*<br/>
HRESULT d’erreur.

### <a name="return-value"></a>Valeur de retour

**`true`** Si l’état d’erreur interne a été modifié ; Sinon, **`false`** .

### <a name="remarks"></a>Notes

Cette opération modifie l’état d’erreur uniquement si l’état d’erreur est déjà défini sur S_OK. Cette opération n’a aucun effet si l’état de l’erreur est déjà erreur, annulé, terminé ou fermé.
