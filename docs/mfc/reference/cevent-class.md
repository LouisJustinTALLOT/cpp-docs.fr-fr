---
title: CEvent (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8450f4b4105f5302750ea0f369d0e6c1dc2925ab
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950883"
---
# <a name="cevent-class"></a>CEvent (classe)
Représente un événement, qui est un objet de synchronisation qui permet à un thread de notifier à un autre qu’un événement s’est produit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CEvent : public CSyncObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CEvent::CEvent](#cevent)|Construit un objet `CEvent`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CEvent::PulseEvent](#pulseevent)|Définit l’événement disponible (signalé), libère les threads en attente et affecte à l’événement non disponible ("non signalé").|  
|[CEvent::ResetEvent](#resetevent)|Définit l’événement indisponible ("non signalé").|  
|[CEvent::SetEvent](#setevent)|Affecte à l’événement disponible (signalé) et libère tous les threads en attente.|  
|[CEvent::Unlock](#unlock)|Libère l’objet d’événement.|  
  
## <a name="remarks"></a>Notes  
 Les événements sont utiles lorsqu’un thread doit savoir à quel moment effectuer sa tâche. Par exemple, un thread qui copie les données vers une archive de données doit être averti lorsque de nouvelles données sont disponibles. En utilisant un `CEvent` objet de notifier le thread de copie lorsque de nouvelles données sont disponibles, le thread peut effectuer sa tâche dès que possible.  
  
 `CEvent` objets ont deux types : automatique et manuel.  
  
 Automatique `CEvent` objet retourne automatiquement à l’état (non disponible) non signalé après au moins un thread est libéré. Par défaut, un `CEvent` objet est automatique, sauf si vous passez `TRUE` pour le *bManualReset* paramètre pendant la construction.  
  
 Un manuel `CEvent` objet reste dans l’état défini par [SetEvent](#setevent) ou [ResetEvent](#resetevent) jusqu'à ce que l’autre fonction est appelée. Création manuelle de `CEvent` de l’objet, passez `TRUE` pour la `bManualReset` paramètre pendant la construction.  
  
 Pour utiliser un `CEvent` de l’objet, construisez la `CEvent` lorsqu’il est nécessaire de l’objet. Spécifiez le nom de l’événement que vous souhaitez attendre et également spécifier que votre application doit initialement êtes bien le propriétaire. Vous pouvez ensuite accéder à l’événement lorsque le constructeur retourne. Appelez [SetEvent](#setevent) au signal (afin de rendre disponible) l’objet d’événement et puis appelez [Unlock](#unlock) lorsque vous avez terminé l’accès à la ressource contrôlée.  
  
 Une autre méthode pour l’utilisation de `CEvent` objets consiste à ajouter une variable de type `CEvent` comme membre de données à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlée, appelez le constructeur de la `CEvent` membre de données et spécifier si l’événement est signalé initialement et également specifythe type d’objet d’événement souhaité, le nom de l’événement (si elle est utilisée dans le processus limites) et les attributs de sécurité que vous souhaitez.  
  
 Pour accéder à une ressource contrôlée par un `CEvent` de l’objet de cette manière, commencez par créer une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou type [CMultiLock](../../mfc/reference/cmultilock-class.md) dans la méthode d’accès de votre ressource. Appelez ensuite la `Lock` méthode de l’objet verrou (par exemple, [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). À ce stade, votre thread sera soit accéder à la ressource, attendez que la ressource à être publié et accéder ou attendez que la ressource doit être libéré, le délai d’attente et ne parviennent pas à accéder à la ressource. Dans tous les cas, votre ressource a été utilisée de manière thread-safe. Pour libérer la ressource, appelez `SetEvent` pour signaler l’objet d’événement, puis utiliser le `Unlock` de l’objet verrou (méthode) (par exemple, [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), ou laisser l’objet verrou se trouvent hors de portée.  
  
 Pour plus d’informations sur l’utilisation de `CEvent` , consultez [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxmt.h  
  
##  <a name="cevent"></a>  CEvent::CEvent  
 Construit un nommé ou sans nom `CEvent` objet.  
  
```  
CEvent(
    BOOL bInitiallyOwn = FALSE,  
    BOOL bManualReset = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *bInitiallyOwn*  
 Si **TRUE**, le thread pour la `CMultilock` ou `CSingleLock` objet est activé. Dans le cas contraire, tous les threads qui souhaitent accéder à la ressource doivent attendre.  
  
 *bManualReset*  
 Si **TRUE**, spécifie que l’objet d’événement est un événement manuel, sinon l’objet d’événement est un événement automatique.  
  
 *Caractère*  
 Nom de l'objet `CEvent`. Doit être fourni si l’objet doit être utilisé au-delà des limites de processus. Si le nom correspond à un événement existant, le constructeur crée un nouveau `CEvent` objet qui fait référence à l’événement du même nom. Si le nom correspond à un objet de synchronisation existant n’est pas un événement, la construction échoue. Si **NULL**, le nom doit être null.  
  
 *lpsaAttribute*  
 Attributs de sécurité pour l’objet d’événement. Pour obtenir une description complète de cette structure, consultez [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Accéder ou de libérer un `CEvent` d’objet, de créer un [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) objet et appeler ses [verrou](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) fonctions membres.  
  
 Pour modifier l’état d’un `CEvent` objet signalé (threads de ne pas ont à attendre), appelez [SetEvent](#setevent) ou [PulseEvent](#pulseevent). Pour définir l’état d’un `CEvent` objet à "non signalé" (threads doivent attendre), appelez [ResetEvent](#resetevent).  
  
> [!IMPORTANT]
>  Après avoir créé le `CEvent` de l’objet, utilisez [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) pour vous assurer que le mutex n’existe pas déjà. Si le mutex n’existait inattendu, cela peut indiquer un processus non autorisé est occupation et peut être intention d’utiliser le mutex à des fins malveillantes. Dans ce cas, la procédure recommandée en termes de sécurité doit fermer le handle et poursuit comme si une défaillance s’est produite lors de la création de l’objet.  
  
##  <a name="pulseevent"></a>  CEvent::PulseEvent  
 Définit l’état de l’événement signalé (disponible), libère tous les threads en attente et réinitialise à "non signalé" (non disponible) automatiquement.  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fonction a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si l’événement est manuel, tous les threads en attente sont publiées, l’événement est défini à "non signalé", et `PulseEvent` retourne. Si l’événement est automatique, un seul thread est lancé, l’événement est défini à "non signalé", et `PulseEvent` retourne.  
  
 Si aucun thread en attente ou aucun thread ne puisse être libérée immédiatement, `PulseEvent` définit l’état de l’événement à "non signalé" et le retourne.  
  
 `PulseEvent` utilise Win32 sous-jacent `PulseEvent` fonction, qui peut être bientôt supprimée à partir de l’état d’attente par un appel de procédure asynchrone en mode noyau. Par conséquent, `PulseEvent` n’est pas fiable et ne doit pas être utilisé par les nouvelles applications. Pour plus d’informations, consultez la [PulseEvent fonction](http://msdn.microsoft.com/library/windows/desktop/ms684914).  
  
##  <a name="resetevent"></a>  CEvent::ResetEvent  
 Définit l’état de l’événement à "non signalé" jusqu'à ce que le défini explicitement à signalé par le [SetEvent](#setevent) fonction membre.  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fonction a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Ainsi, tous les threads qui souhaitent accéder à cet événement d’attente.  
  
 Cette fonction membre n’est pas utilisée par les événements automatiques.  
  
##  <a name="setevent"></a>  CEvent::SetEvent  
 Définit l’état de l’événement signalé, libérer les threads en attente.  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fonction a réussi, sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si l’événement est manuelle, l’événement reste signalé jusqu'à ce que [ResetEvent](#resetevent) est appelée. Plusieurs threads peuvent être lancées dans ce cas. Si l’événement est automatique, l’événement reste signalé jusqu'à ce qu’un seul thread est libéré. Le système définit ensuite l’état de l’événement à "non signalé". Si aucun thread n’est en attente, l’état reste signalé jusqu'à ce qu’un seul thread est libéré.  
  
##  <a name="unlock"></a>  CEvent::Unlock  
 Libère l’objet d’événement.  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le thread propriétaire de l’objet d’événement et l’événement est un événement automatique ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre est appelée par les threads qui possèdent actuellement un événement automatique pour libérer une fois terminés, si leur objet verrou doit être réutilisé. Si l’objet de verrouillage n’est ne pas à être réutilisé, cette fonction est appelée par le destructeur de l’objet de verrouillage.  
  
## <a name="see-also"></a>Voir aussi  
 [CSyncObject (classe)](../../mfc/reference/csyncobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)

