---
title: CSingleLock (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 1ae72b7c9c2acf4fa8600903061869ba049cd58c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372967"
---
# <a name="csinglelock-class"></a>CSingleLock (classe)
Représente le mécanisme de contrôle d'accès utilisé dans le contrôle de l'accès à une ressource dans un programme multithread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSingleLock  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSingleLock::CSingleLock](#csinglelock)|Construit un objet `CSingleLock`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSingleLock::IsLocked](#islocked)|Détermine si l’objet est verrouillé.|  
|[CSingleLock::Lock](#lock)|Attend sur un objet de synchronisation.|  
|[CSingleLock::Unlock](#unlock)|Libère un objet de synchronisation.|  
  
## <a name="remarks"></a>Notes  
 `CSingleLock` ne dispose pas d’une classe de base.  
  
 Pour pouvoir utiliser les classes de synchronisation [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), et [CEvent](../../mfc/reference/cevent-class.md), vous devez créer un `CSingleLock` ou [CMultiLock](../../mfc/reference/cmultilock-class.md) objet attendent et libérer l’objet de synchronisation. Utilisez `CSingleLock` lorsque vous devez uniquement d’attente sur un objet à la fois. Utilisez **CMultiLock** lorsqu’il existe plusieurs objets que vous pouvez utiliser à un moment donné.  
  
 Pour utiliser un `CSingleLock` d’objet, appeler son constructeur à l’intérieur d’une fonction membre de classe de la ressource contrôlée. Appelez ensuite la [IsLocked](#islocked) fonction membre pour déterminer si la ressource est disponible. S’il s’agit, continuer avec le reste de la fonction membre. Si la ressource n’est pas disponible, attendre un certain temps pour la ressource doit être publié ou renvoient une erreur. Après l’utilisation de la ressource est terminée, vous devez soit appeler le [Unlock](#unlock) fonctionner si le `CSingleLock` objet doit être réutilisé, ou autoriser le `CSingleLock` objet point d’être détruit.  
  
 `CSingleLock` les objets nécessitent la présence d’un objet dérivé de [CSyncObject](../../mfc/reference/csyncobject-class.md). Cela est généralement une donnée membre de classe de la ressource contrôlée. Pour plus d’informations sur l’utilisation de `CSingleLock` , consultez l’article [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CSingleLock`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxmt.h  
  
##  <a name="csinglelock"></a>  CSingleLock::CSingleLock  
 Construit un objet `CSingleLock`.  
  
```  
explicit CSingleLock(
    CSyncObject* pObject,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 `pObject`  
 Pointe vers l’objet de synchronisation accessible. Ne peut pas être **NULL**.  
  
 `bInitialLock`  
 Spécifie s’il faut initialement essayer d’accéder à l’objet fourni.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est généralement appelée à partir d’une fonction membre d’accès de la ressource contrôlée.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]  
  
##  <a name="islocked"></a>  CSingleLock::IsLocked  
 Détermine si l’objet associé à la `CSingleLock` objet est "non signalé" (non disponible).  
  
```  
BOOL IsLocked();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’objet est verrouillé ; Sinon, 0.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]  
  
##  <a name="lock"></a>  CSingleLock::Lock  
 Appelez cette fonction pour accéder à la ressource contrôlée par l’objet de synchronisation fourni à la `CSingleLock` constructeur.  
  
```  
BOOL Lock(DWORD dwTimeOut = INFINITE);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwTimeOut*  
 Spécifie la quantité de temps d’attente pour l’objet de synchronisation soit disponible (signalée). Si **infinie**, `Lock` attendra jusqu'à ce que l’objet est signalé avant de retourner.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fonction a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Si l’objet de synchronisation est signalé, `Lock` retournera avec succès et le thread possède maintenant l’objet. Si l’objet de synchronisation est "non signalé" (non disponible), `Lock` attend l’objet de synchronisation soient signalés jusqu’au nombre de millisecondes spécifié dans le *dwTimeOut* paramètre. Si l’objet de synchronisation s’est pas signalé dans le laps de temps, `Lock` échoue.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
##  <a name="unlock"></a>  CSingleLock::Unlock  
 Libère l’objet de synchronisation détenu par `CSingleLock`.  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `lCount`  
 Nombre d’accès à libérer. Doit être supérieure à 0. Si la quantité spécifiée peut provoquer le nombre de l’objet dépasse sa limite maximale, le nombre n’est pas modifié et la fonction retourne **FALSE**.  
  
 `lPrevCount`  
 Pointe vers une variable devant recevoir le décompte précédent de l’objet de synchronisation. Si **NULL**, le compteur précédent n’est pas retourné.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fonction a réussi ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est appelée par `CSingleLock`du destructeur.  
  
 Si vous avez besoin libérer plus d’un nombre d’accès d’un sémaphore, utilisez la deuxième forme de `Unlock` et spécifiez le nombre d’accès à libérer.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CMultiLock, classe](../../mfc/reference/cmultilock-class.md)
