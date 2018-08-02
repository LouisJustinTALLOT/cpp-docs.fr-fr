---
title: Asyncbase, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
dev_langs:
- C++
helpviewer_keywords:
- AsyncBase class
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 92add8f79abd3aac7c11142fa67ea3b4bcd237d5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466200"
---
# <a name="asyncbase-class"></a>AsyncBase (classe)
Implémente la machine d'état asynchrone du Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Paramètres  
 *TComplete*  
 Un gestionnaire d’événements qui est appelé lorsqu’une opération asynchrone se termine.  
  
 *TProgress*  
 Un gestionnaire d’événements qui est appelé lorsqu’une opération asynchrone en cours d’exécution signale la progression actuelle de l’opération.  
  
 *resultType*  
 Parmi les [AsyncResultType](../windows/asyncresulttype-enumeration.md) valeurs d’énumération. Par défaut, SingleResult.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[AsyncBase::AsyncBase, constructeur](../windows/asyncbase-asyncbase-constructor.md)|Initialise une instance de la **AsyncBase** classe.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[AsyncBase::Cancel, méthode](../windows/asyncbase-cancel-method.md)|Annule une opération asynchrone.|  
|[AsyncBase::Close, méthode](../windows/asyncbase-close-method.md)|Ferme l’opération asynchrone.|  
|[AsyncBase::FireCompletion, méthode](../windows/asyncbase-firecompletion-method.md)|Appelle le Gestionnaire d’événements de saisie semi-automatique, ou réinitialise le délégué de progression interne.|  
|[AsyncBase::FireProgress, méthode](../windows/asyncbase-fireprogress-method.md)|Appelle le Gestionnaire d’événements de progression actuel.|  
|[AsyncBase::get_ErrorCode, méthode](../windows/asyncbase-get-errorcode-method.md)|Récupère le code d’erreur pour l’opération asynchrone actuelle.|  
|[AsyncBase::get_Id, méthode](../windows/asyncbase-get-id-method.md)|Récupère le handle de l’opération asynchrone.|  
|[AsyncBase::get_Status, méthode](../windows/asyncbase-get-status-method.md)|Récupère une valeur qui indique l’état de l’opération asynchrone.|  
|[AsyncBase::GetOnComplete, méthode](../windows/asyncbase-getoncomplete-method.md)|Copie l’adresse du Gestionnaire d’événements de saisie semi-automatique actuelle à la variable spécifiée.|  
|[AsyncBase::GetOnProgress, méthode](../windows/asyncbase-getonprogress-method.md)|Copie l’adresse du Gestionnaire d’événements de progression actuel à la variable spécifiée.|  
|[AsyncBase::put_Id, méthode](../windows/asyncbase-put-id-method.md)|Définit le handle de l’opération asynchrone.|  
|[AsyncBase::PutOnComplete, méthode](../windows/asyncbase-putoncomplete-method.md)|Définit l’adresse du Gestionnaire d’événements de saisie semi-automatique à la valeur spécifiée.|  
|[AsyncBase::PutOnProgress, méthode](../windows/asyncbase-putonprogress-method.md)|Définit l’adresse du Gestionnaire d’événements de progression à la valeur spécifiée.|  
|[AsyncBase::Start, méthode](../windows/asyncbase-start-method.md)|Démarre l’opération asynchrone.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[AsyncBase::CheckValidStateForDelegateCall, méthode](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|Teste si les propriétés de délégué peuvent être modifiées dans l’état asynchrone actuelle.|  
|[AsyncBase::CheckValidStateForResultsCall, méthode](../windows/asyncbase-checkvalidstateforresultscall-method.md)|Teste si les résultats d’une opération asynchrone peuvent être collectées dans l’état asynchrone actuelle.|  
|[AsyncBase::ContinueAsyncOperation, méthode](../windows/asyncbase-continueasyncoperation-method.md)|Détermine si l’opération asynchrone doit poursuivre le traitement ou qu’il doit s’arrêter.|  
|[AsyncBase::CurrentStatus, méthode](../windows/asyncbase-currentstatus-method.md)|Récupère l’état de l’opération asynchrone actuelle.|  
|[AsyncBase::ErrorCode, méthode](../windows/asyncbase-errorcode-method.md)|Récupère le code d’erreur pour l’opération asynchrone actuelle.|  
|[AsyncBase::OnCancel, méthode](../windows/asyncbase-oncancel-method.md)|En cas de substitution dans une classe dérivée, annule une opération asynchrone.|  
|[AsyncBase::OnClose, méthode](../windows/asyncbase-onclose-method.md)|En cas de substitution dans une classe dérivée, ferme une opération asynchrone.|  
|[AsyncBase::OnStart, méthode](../windows/asyncbase-onstart-method.md)|En cas de substitution dans une classe dérivée, démarre une opération asynchrone.|  
|[AsyncBase::TryTransitionToCompleted, méthode](../windows/asyncbase-trytransitiontocompleted-method.md)|Indique si l’opération asynchrone en cours est terminée.|  
|[AsyncBase::TryTransitionToError, méthode](../windows/asyncbase-trytransitiontoerror-method.md)|Indique si le code d’erreur spécifié peut modifier l’état d’erreur interne.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `AsyncBase`  
  
 `AsyncBase`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)