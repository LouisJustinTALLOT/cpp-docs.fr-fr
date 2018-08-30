---
title: CMutex, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
dev_langs:
- C++
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8162ba8ffe70225980819d45ea55fb8427abd294
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196672"
---
# <a name="cmutex-class"></a>CMutex, classe
Représente un « mutex », un objet de synchronisation qui permet à un thread l’accès mutuellement exclusif à une ressource.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMutex : public CSyncObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMutex::CMutex](#cmutex)|Construit un objet `CMutex`.|  
  
## <a name="remarks"></a>Notes  
 Les mutex sont utiles lorsque qu’un seul thread à la fois peut être autorisé à modifier des données ou une autre ressource contrôlée. Par exemple, l’ajout de nœuds à une liste liée est un processus qui ne doivent être autorisé par un seul thread à la fois. En utilisant un `CMutex` objet pour contrôler la liste liée, uniquement un seul thread à la fois peut accéder à la liste.  
  
 Pour utiliser un `CMutex` d’objet, de construire le `CMutex` lorsqu’il est nécessaire de l’objet. Spécifiez le nom du mutex voulez-vous attendre, et que votre application doit initialement êtes bien le propriétaire. Vous pouvez ensuite accéder le mutex lorsque le constructeur est retournée. Appelez [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) lorsque vous avez terminé l’accès à la ressource contrôlée.  
  
 Une autre méthode pour l’utilisation de `CMutex` objets consiste à ajouter une variable de type `CMutex` comme membre de données à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlée, appelez le constructeur de la `CMutex` membre de données en spécifiant si le mutex est initialement la propriété, le nom du mutex (s’il doit être utilisé au-delà des limites de processus) et les attributs de sécurité souhaités.  
  
 Pour accéder aux ressources contrôlées par `CMutex` objets de cette manière, créez tout d’abord une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou type [CMultiLock](../../mfc/reference/cmultilock-class.md) dans la fonction membre de l’accès de votre ressource. Appelez ensuite l’objet verrou `Lock` fonction membre (par exemple, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). À ce stade, votre thread sera soit accéder à la ressource, attendez que la ressource à libérée et y accéder ou attendez que la ressource doit être publié et le délai d’attente, ne parvient pas à accéder à la ressource. Dans tous les cas, votre ressource a accédé de manière thread-safe. Pour libérer la ressource, utilisez l’objet verrou `Unlock` fonction membre (par exemple, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), ou autorise l’objet verrou se situent hors de portée.  
  
 Pour plus d’informations sur l’utilisation de `CMutex` objets, consultez l’article [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxmt.h  
  
##  <a name="cmutex"></a>  CMutex::CMutex  
 Construit un nommé ou sans nom `CMutex` objet.  
  
```  
CMutex(
    BOOL bInitiallyOwn = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *bInitiallyOwn*  
 Spécifie si le thread créant la `CMutex` objet a initialement accès à la ressource contrôlée par le mutex.  
  
 *Caractère*  
 Nom de l'objet `CMutex`. Si le mutex une autre portant le même nom existe, *le caractère* doit être fourni si l’objet doit être utilisé au-delà des limites de processus. Si **NULL**, le mutex sera sans nom. Si le nom correspond à un mutex existant, le constructeur crée quand même un `CMutex` objet qui fait référence à l’exclusion mutuelle de ce nom. Si le nom correspond à un objet de synchronisation existant qui n’est pas un mutex, la construction échoue.  
  
 *lpsaAttribute*  
 Attributs de sécurité de l’objet mutex. Pour obtenir une description complète de cette structure, consultez [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Pour accéder à ou libérer un `CMutex` d’objet, de créer un [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) objet et appelez ses [verrou](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) fonctions membres. Si le `CMutex` objet est en cours d’utilisation autonome, appeler ses `Unlock` fonction membre pour le libérer.  
  
> [!IMPORTANT]
>  Après avoir créé le `CMutex` de l’objet, utilisez [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) pour vous assurer que le mutex n’existait pas. Si le mutex n’existait inattendu, cela peut indiquer un processus non fiable est l’occupation et peut être ayant l’intention d’utiliser le mutex à des fins malveillantes. Dans ce cas, la procédure en termes de sécurité recommandée consiste à fermer le handle et continuer comme si une défaillance s’est produite lors de la création de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [CSyncObject, classe](../../mfc/reference/csyncobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



