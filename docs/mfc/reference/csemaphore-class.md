---
title: CSemaphore (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
dev_langs:
- C++
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b00e7e1bc42317b4028264a49006b40de4fbb507
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078880"
---
# <a name="csemaphore-class"></a>CSemaphore (classe)
Un objet de classe `CSemaphore` représente un « sémaphore », un objet de synchronisation qui permet à un nombre limité de threads dans un ou plusieurs processus pour accéder à un maintien un décompte du nombre de threads qui accèdent actuellement à une ressource spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSemaphore : public CSyncObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSemaphore::CSemaphore](#csemaphore)|Construit un objet `CSemaphore`.|  
  
## <a name="remarks"></a>Notes  
 Sémaphores nommés sont utiles pour contrôler l’accès à une ressource partagée qui peut prendre uniquement en charge un nombre limité d’utilisateurs. Le nombre actuel de la `CSemaphore` objet est le nombre d’utilisateurs supplémentaires autorisés. Lorsque le décompte atteint zéro, toutes les tentatives d’utiliser la ressource contrôlée par le `CSemaphore` objet sera insérée dans une file d’attente système et ils attendre un délai d’attente ou le nombre se situe au-dessus de 0. Le nombre maximal d’utilisateurs pouvant accéder simultanément à la ressource contrôlée est spécifié pendant la construction de la `CSemaphore` objet.  
  
 Pour utiliser un `CSemaphore` de l’objet, construisez la `CSemaphore` lorsqu’il est nécessaire de l’objet. Spécifiez le nom du sémaphore que vous souhaitez attendre, et il doit initialement propriétaire de votre application. Vous pouvez ensuite accéder le sémaphore lorsque le constructeur est retournée. Appelez [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) lorsque vous avez terminé l’accès à la ressource contrôlée.  
  
 Une autre méthode pour l’utilisation de `CSemaphore` objets consiste à ajouter une variable de type `CSemaphore` comme membre de données à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlée, appelez le constructeur de la `CSemaphore` membre de données en spécifiant l’initiale accès nombre, nombre maximal d’accès, nom du sémaphore (si elle est utilisée dans des limites de processus) et les attributs de sécurité souhaités.  
  
 Pour accéder aux ressources contrôlé par `CSemaphore` les objets de cette manière, créez tout d’abord une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou type [CMultiLock](../../mfc/reference/cmultilock-class.md) dans la fonction membre de l’accès de votre ressource. Appelez ensuite l’objet de verrouillage `Lock` fonction membre (par exemple, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). À ce stade, votre thread sera soit accéder à la ressource, attendez que la ressource à être publié et accéder ou attendez que la ressource doit être publié et le délai d’expiration, ne parvient pas à accéder à la ressource. Dans tous les cas, votre ressource a été utilisée de manière thread-safe. Pour libérer la ressource, utilisez l’objet de verrouillage `Unlock` fonction membre (par exemple, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), ou autorise l’objet verrou se trouvent hors de portée.  
  
 Vous pouvez également créer un `CSemaphore` autonome de l’objet et y accéder explicitement avant de tenter d’accéder à la ressource contrôlée. Cette méthode, lors de la façon la plus claire à une personne lisant votre code source, est plus sujette aux erreurs.  
  
 Pour plus d’informations sur l’utilisation de `CSemaphore` , consultez l’article [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxmt.h  
  
##  <a name="csemaphore"></a>  CSemaphore::CSemaphore  
 Construit un nommé ou sans nom `CSemaphore` objet.  
  
```  
CSemaphore(
    LONG lInitialCount = 1,  
    LONG lMaxCount = 1,  
    LPCTSTR pstrName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *lInitialCount*  
 Le décompte d’utilisation initial pour le sémaphore. Doit être supérieur ou égal à 0 et inférieur ou égal à *lMaxCount*.  
  
 *lMaxCount*  
 Le nombre maximal d’utilisation pour le sémaphore. Doit être supérieure à 0.  
  
 *pstrName*  
 Le nom du sémaphore. Doit être fourni si le sémaphore est accessible au-delà des limites de processus. Si `NULL`, l’objet est sans nom. Si le nom correspond à un sémaphore existant, le constructeur crée un nouveau `CSemaphore` objet qui référence le sémaphore de ce nom. Si le nom correspond à un objet de synchronisation existant n’est pas un sémaphore, la construction échoue.  
  
 *lpsaAttributes*  
 Attributs de sécurité pour l’objet de sémaphore. Pour obtenir une description complète de cette structure, consultez [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Accéder ou de libérer un `CSemaphore` d’objet, de créer un [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) objet et appeler ses [verrou](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) fonctions membres.  
  
> [!IMPORTANT]
>  Après avoir créé le `CSemaphore` de l’objet, utilisez [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) pour vous assurer que le mutex n’existait pas. Si le mutex n’existait inattendu, cela peut indiquer un processus non autorisé est occupation et peut être intention d’utiliser le mutex à des fins malveillantes. Dans ce cas, la procédure recommandée en termes de sécurité doit fermer le handle et poursuit comme si une défaillance s’est produite lors de la création de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [CSyncObject (classe)](../../mfc/reference/csyncobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



