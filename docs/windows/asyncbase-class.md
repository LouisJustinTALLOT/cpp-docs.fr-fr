---
title: Asyncbase, classe | Microsoft Docs
ms.custom: ''
ms.date: 09/28/2018
ms.technology:
- cpp-windows
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
- async/Microsoft::WRL::AsyncBase::Start
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs:
- C++
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
- Microsoft::WRL::AsyncBase::Start method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d74e3cb74634a83d9f03b74527f0965c7a79f016
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235949"
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

template <
   typename TComplete,
   AsyncResultType resultType
>
class AsyncBase<TComplete, Details::Nil, resultType> : public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>Paramètres

*TComplete*<br/>
Un gestionnaire d’événements qui est appelé lorsqu’une opération asynchrone se termine.

*TProgress*<br/>
Un gestionnaire d’événements qui est appelé lorsqu’une opération asynchrone en cours d’exécution signale la progression actuelle de l’opération.

*resultType*<br/>
Parmi les [AsyncResultType](../windows/asyncresulttype-enumeration.md) valeurs d’énumération. Par défaut, `SingleResult`.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

Nom                               | Description
---------------------------------- | -------------------------------------------------
[AsyncBase::AsyncBase](#asyncbase) | Initialise une instance de la classe `AsyncBase`.

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                         | Description
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase::Cancel](#cancel)                 | Annule une opération asynchrone.
[AsyncBase::Close](#close)                   | Ferme l’opération asynchrone.
[AsyncBase::FireCompletion](#firecompletion) | Appelle le Gestionnaire d’événements de saisie semi-automatique, ou réinitialise le délégué de progression interne.
[AsyncBase::FireProgress](#fireprogress)     | Appelle le Gestionnaire d’événements de progression actuel.
[AsyncBase::get_ErrorCode](#get-errorcode)   | Récupère le code d’erreur pour l’opération asynchrone actuelle.
[AsyncBase::get_Id](#get-id)                 | Récupère le handle de l’opération asynchrone.
[AsyncBase::get_Status](#get-status)         | Récupère une valeur qui indique l’état de l’opération asynchrone.
[AsyncBase::GetOnComplete](#getoncomplete)   | Copie l’adresse du Gestionnaire d’événements de saisie semi-automatique actuelle à la variable spécifiée.
[AsyncBase::GetOnProgress](#getonprogress)   | Copie l’adresse du Gestionnaire d’événements de progression actuel à la variable spécifiée.
[AsyncBase::put_Id](#put-id)                 | Définit le handle de l’opération asynchrone.
[AsyncBase::PutOnComplete](#putoncomplete)   | Définit l’adresse du Gestionnaire d’événements de saisie semi-automatique à la valeur spécifiée.
[AsyncBase::PutOnProgress](#putonprogress)   | Définit l’adresse du Gestionnaire d’événements de progression à la valeur spécifiée.
[AsyncBase::Start](#start)                   | Démarre l’opération asynchrone.

### <a name="protected-methods"></a>Méthodes protégées

Nom                                                                         | Description
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase::CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | Teste si les propriétés de délégué peuvent être modifiées dans l’état asynchrone actuelle.
[AsyncBase::CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | Teste si les résultats d’une opération asynchrone peuvent être collectées dans l’état asynchrone actuelle.
[AsyncBase::ContinueAsyncOperation](#continueasyncoperation)                 | Détermine si l’opération asynchrone doit poursuivre le traitement ou qu’il doit s’arrêter.
[AsyncBase::CurrentStatus](#currentstatus)                                   | Récupère l’état de l’opération asynchrone actuelle.
[AsyncBase::ErrorCode](#errorcode)                                           | Récupère le code d’erreur pour l’opération asynchrone actuelle.
[AsyncBase::OnCancel](#oncancel)                                             | En cas de substitution dans une classe dérivée, annule une opération asynchrone.
[AsyncBase::OnClose](#onclose)                                               | En cas de substitution dans une classe dérivée, ferme une opération asynchrone.
[AsyncBase::OnStart](#onstart)                                               | En cas de substitution dans une classe dérivée, démarre une opération asynchrone.
[AsyncBase::TryTransitionToCompleted](#trytransitiontocompleted)             | Indique si l’opération asynchrone en cours est terminée.
[AsyncBase::TryTransitionToError](#trytransitiontoerror)                     | Indique si le code d’erreur spécifié peut modifier l’état d’erreur interne.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Configuration requise

**En-tête :** async.h

**Espace de noms :** Microsoft::WRL

## <a name="asyncbase"></a>AsyncBase::AsyncBase

Initialise une instance de la classe `AsyncBase`.

```cpp
AsyncBase();
```

## <a name="cancel"></a>AsyncBase::Cancel

Annule une opération asynchrone.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Valeur de retour

Par défaut, retourne toujours S_OK.

### <a name="remarks"></a>Notes

`Cancel()` est une implémentation par défaut de `IAsyncInfo::Cancel`, et n’effectue aucun travail réel. Pour réellement annuler une opération asynchrone, remplacer le `OnCancel()` méthode virtuelle pure.

## <a name="checkvalidstatefordelegatecall"></a>AsyncBase::CheckValidStateForDelegateCall

Teste si les propriétés de délégué peuvent être modifiées dans l’état asynchrone actuelle.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Valeur de retour

S_OK si les propriétés de délégué peuvent être modifiées ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="checkvalidstateforresultscall"></a>AsyncBase::CheckValidStateForResultsCall

Teste si les résultats d’une opération asynchrone peuvent être collectées dans l’état asynchrone actuelle.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Valeur de retour

S_OK si les résultats peuvent être collectés ; Sinon, E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="close"></a>AsyncBase::Close

Ferme l’opération asynchrone.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Valeur de retour

S_OK si l’opération se ferme ou est déjà fermé ; Sinon, E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Notes

`Close()` est une implémentation par défaut de `IAsyncInfo::Close`, et n’effectue aucun travail réel. Pour fermer réellement une opération asynchrone, remplacer le `OnClose()` méthode virtuelle pure.

## <a name="continueasyncoperation"></a>AsyncBase::ContinueAsyncOperation

Détermine si l’opération asynchrone doit poursuivre le traitement ou qu’il doit s’arrêter.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Valeur de retour

`true` Si l’état actuel de l’opération asynchrone est *démarré*, ce qui signifie que l’opération doit continuer. Sinon, `false`, ce qui signifie que l’opération doit s’arrêter.

## <a name="currentstatus"></a>AsyncBase::CurrentStatus

Récupère l’état de l’opération asynchrone actuelle.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Paramètres

*status*<br/>
L’emplacement où cette opération stocke l’état actuel.

### <a name="remarks"></a>Notes

Cette opération est thread-safe.

## <a name="errorcode"></a>AsyncBase::ErrorCode

Récupère le code d’erreur pour l’opération asynchrone actuelle.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Paramètres

*Erreur*<br/>
L’emplacement où cette opération stocke le code d’erreur actuel.

### <a name="remarks"></a>Notes

Cette opération est thread-safe.

## <a name="firecompletion"></a>AsyncBase::FireCompletion

Appelle le Gestionnaire d’événements de saisie semi-automatique, ou réinitialise le délégué de progression interne.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Notes

La première version de `FireCompletion()` réinitialise la variable de délégué de progression interne. La deuxième version appelle le Gestionnaire d’événements de saisie semi-automatique si l’opération asynchrone est terminée.

## <a name="fireprogress"></a>AsyncBase::FireProgress

Appelle le Gestionnaire d’événements de progression actuel.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Paramètres

*arg*<br/>
La méthode de gestionnaire d’événements à appeler.

### <a name="remarks"></a>Notes

`ProgressTraits` est dérivé de [ArgTraitsHelper (Structure)](../windows/argtraitshelper-structure.md).

## <a name="get-errorcode"></a>AsyncBase::get_ErrorCode

Récupère le code d’erreur pour l’opération asynchrone actuelle.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Paramètres

*code d’erreur*<br/>
L’emplacement où se trouve le code d’erreur actuel.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL si l’opération asynchrone en cours est fermée.

## <a name="get-id"></a>AsyncBase::get_Id

Récupère le handle de l’opération asynchrone.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
L’emplacement où le handle doit être stocké.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Notes

Cette méthode implémente `IAsyncInfo::get_Id`.

## <a name="get-status"></a>AsyncBase::get_Status

Récupère une valeur qui indique l’état de l’opération asynchrone.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Paramètres

*status*<br/>
L’emplacement où l’état doit être stocké. Pour plus d’informations, consultez `Windows::Foundation::AsyncStatus` énumération.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Notes

Cette méthode implémente `IAsyncInfo::get_Status`.

## <a name="getoncomplete"></a>AsyncBase::GetOnComplete

Copie l’adresse du Gestionnaire d’événements de saisie semi-automatique actuelle à la variable spécifiée.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Paramètres

*completeHandler*<br/>
L’emplacement de stockage de l’adresse du Gestionnaire d’événements de saisie semi-automatique actuel.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="getonprogress"></a>AsyncBase::GetOnProgress

Copie l’adresse du Gestionnaire d’événements de progression actuel à la variable spécifiée.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Paramètres

*progressHandler*<br/>
L’emplacement de stockage de l’adresse du Gestionnaire d’événements de progression actuel.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="oncancel"></a>AsyncBase::OnCancel

En cas de substitution dans une classe dérivée, annule une opération asynchrone.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="onclose"></a>AsyncBase::OnClose

En cas de substitution dans une classe dérivée, ferme une opération asynchrone.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="onstart"></a>AsyncBase::OnStart

En cas de substitution dans une classe dérivée, démarre une opération asynchrone.

```cpp
virtual void OnStart(
   void
) = 0;
```

## <a name="put-id"></a>AsyncBase::put_Id

Définit le handle de l’opération asynchrone.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Paramètres

*ID*<br/>
Un handle différente de zéro.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_INVALIDARG ou E_ILLEGAL_METHOD_CALL.

## <a name="putoncomplete"></a>AsyncBase::PutOnComplete

Définit l’adresse du Gestionnaire d’événements de saisie semi-automatique à la valeur spécifiée.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Paramètres

*completeHandler*<br/>
L’adresse à laquelle le Gestionnaire d’événements de saisie semi-automatique est défini.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="putonprogress"></a>AsyncBase::PutOnProgress

Définit l’adresse du Gestionnaire d’événements de progression à la valeur spécifiée.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Paramètres

*progressHandler*<br/>
L’adresse à laquelle le Gestionnaire d’événements de progression est défini.

### <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, E_ILLEGAL_METHOD_CALL.

## <a name="start"></a>AsyncBase::Start

Démarre l’opération asynchrone.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Valeur de retour

S_OK si l’opération démarre ou est déjà démarré ; Sinon, E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Notes

`Start()` est une implémentation par défaut de `IAsyncInfo::Start`, et n’effectue aucun travail réel. Pour lancer une opération asynchrone, remplacer le `OnStart()` méthode virtuelle pure.

## <a name="trytransitiontocompleted"></a>AsyncBase::TryTransitionToCompleted

Indique si l’opération asynchrone en cours est terminée.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Valeur de retour

`true` Si l’opération asynchrone est terminée ; Sinon, `false`.

## <a name="trytransitiontoerror"></a>AsyncBase::TryTransitionToError

Indique si le code d’erreur spécifié peut modifier l’état d’erreur interne.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Paramètres

*Erreur*<br/>
Une erreur HRESULT.

### <a name="return-value"></a>Valeur de retour

`true` Si l’état d’erreur interne a été modifié ; Sinon, `false`.

### <a name="remarks"></a>Notes

Cette opération modifie l’état d’erreur uniquement si l’état d’erreur est déjà définie à S_OK. Cette opération n’a aucun effet si l’état d’erreur est déjà erreur, annulé, terminé ou fermé.
