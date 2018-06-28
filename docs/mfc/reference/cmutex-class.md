---
title: Classe CMutex | Documents Microsoft
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
ms.openlocfilehash: f3bde85e64fe8593ec2637e767e8c3c70d3b8200
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038075"
---
# <a name="cmutex-class"></a>Classe CMutex
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
  
 Pour utiliser un `CMutex` de l’objet, construisez la `CMutex` lorsqu’il est nécessaire de l’objet. Spécifiez le nom du mutex que vous souhaitez attendre, et il doit initialement propriétaire de votre application. Vous pouvez ensuite accéder mutex lorsque le constructeur est retournée. Appelez [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) lorsque vous avez terminé l’accès à la ressource contrôlée.  
  
 Une autre méthode pour l’utilisation de `CMutex` objets consiste à ajouter une variable de type `CMutex` comme membre de données à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlée, appelez le constructeur de la `CMutex` membre de données en spécifiant si le mutex est possédé initialement, le nom du mutex (si elle est utilisée dans des limites de processus) et les attributs de sécurité souhaités.  
  
 Pour accéder aux ressources contrôlé par `CMutex` les objets de cette manière, créez tout d’abord une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou type [CMultiLock](../../mfc/reference/cmultilock-class.md) dans la fonction membre de l’accès de votre ressource. Appelez ensuite l’objet de verrouillage `Lock` fonction membre (par exemple, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). À ce stade, votre thread sera soit accéder à la ressource, attendez que la ressource à être publié et accéder ou attendez que la ressource doit être publié et le délai d’expiration, ne parvient pas à accéder à la ressource. Dans tous les cas, votre ressource a été utilisée de manière thread-safe. Pour libérer la ressource, utilisez l’objet de verrouillage `Unlock` fonction membre (par exemple, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), ou autorise l’objet verrou se trouvent hors de portée.  
  
 Pour plus d’informations sur l’utilisation de `CMutex` , consultez l’article [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
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
 Spécifie si la création du thread du `CMutex` objet a initialement l’accès à la ressource contrôlée par le mutex.  
  
 *Caractère*  
 Nom de l'objet `CMutex`. Si un autre mutex portant le même nom existe, *le caractère* doit être fournie si l’objet doit être utilisé au-delà des limites de processus. Si **NULL**, l’exclusion mutuelle est sans nom. Si le nom correspond à un mutex existant, le constructeur crée un nouveau `CMutex` objet qui fait référence à l’exclusion mutuelle de ce nom. Si le nom correspond à un objet de synchronisation existant n’est pas un mutex, la construction échoue.  
  
 *lpsaAttribute*  
 Attributs de sécurité pour l’objet mutex. Pour obtenir une description complète de cette structure, consultez [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Accéder ou de libérer un `CMutex` d’objet, de créer un [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) objet et appeler ses [verrou](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) fonctions membres. Si le `CMutex` utilisation de l’objet autonome, appelez sa `Unlock` fonction membre pour le libérer.  
  
> [!IMPORTANT]
>  Après avoir créé le `CMutex` de l’objet, utilisez [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) pour vous assurer que le mutex n’existait pas. Si le mutex n’existait inattendu, cela peut indiquer un processus non autorisé est occupation et peut être intention d’utiliser le mutex à des fins malveillantes. Dans ce cas, la procédure recommandée en termes de sécurité doit fermer le handle et poursuit comme si une défaillance s’est produite lors de la création de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [CSyncObject (classe)](../../mfc/reference/csyncobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



