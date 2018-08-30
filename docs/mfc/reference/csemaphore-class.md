---
title: CSemaphore, classe | Microsoft Docs
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
ms.openlocfilehash: feb595a5b963e3898c1ce467a5a0487062dd9bca
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198509"
---
# <a name="csemaphore-class"></a>CSemaphore, classe
Un objet de classe `CSemaphore` représente un « sémaphore », un objet de synchronisation qui permet un nombre limité de threads dans un ou plusieurs processus pour accéder à un maintien d’un décompte du nombre de threads qui accèdent actuellement à une ressource spécifiée.  
  
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
 Sémaphores sont utiles dans le contrôle de l’accès à une ressource partagée qui peut prendre uniquement en charge un nombre limité d’utilisateurs. Le nombre actuel de la `CSemaphore` objet est le nombre d’utilisateurs supplémentaires autorisés. Lorsque le décompte atteint zéro, toutes les tentatives d’utiliser les ressources contrôlées par le `CSemaphore` objet sera insérée dans une file d’attente système et ils attendre un délai d’attente ou le nombre s’élève au-dessus de 0. Le nombre maximal d’utilisateurs pouvant accéder simultanément à la ressource contrôlée est spécifié pendant la construction de la `CSemaphore` objet.  
  
 Pour utiliser un `CSemaphore` d’objet, de construire le `CSemaphore` lorsqu’il est nécessaire de l’objet. Spécifiez le nom du sémaphore voulez-vous attendre, et que votre application doit initialement êtes bien le propriétaire. Vous pouvez ensuite accéder le sémaphore lorsque le constructeur est retournée. Appelez [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) lorsque vous avez terminé l’accès à la ressource contrôlée.  
  
 Une autre méthode pour l’utilisation de `CSemaphore` objets consiste à ajouter une variable de type `CSemaphore` comme membre de données à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlée, appelez le constructeur de la `CSemaphore` membre de données en spécifiant l’initiale accéder count, nombre maximal d’accès, nom du sémaphore (s’il doit être utilisé au-delà des limites de processus) et les attributs de sécurité souhaités.  
  
 Pour accéder aux ressources contrôlées par `CSemaphore` objets de cette manière, créez tout d’abord une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou type [CMultiLock](../../mfc/reference/cmultilock-class.md) dans la fonction membre de l’accès de votre ressource. Appelez ensuite l’objet verrou `Lock` fonction membre (par exemple, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). À ce stade, votre thread sera soit accéder à la ressource, attendez que la ressource à libérée et y accéder ou attendez que la ressource doit être publié et le délai d’attente, ne parvient pas à accéder à la ressource. Dans tous les cas, votre ressource a accédé de manière thread-safe. Pour libérer la ressource, utilisez l’objet verrou `Unlock` fonction membre (par exemple, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), ou autorise l’objet verrou se situent hors de portée.  
  
 Vous pouvez également créer un `CSemaphore` objet autonome et y accéder explicitement avant de tenter d’accéder à la ressource contrôlée. Cette méthode, lors de la façon la plus claire à une personne lisant votre code source, est plus sujette aux erreurs.  
  
 Pour plus d’informations sur l’utilisation `CSemaphore` objets, consultez l’article [Multithreading : comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
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
 Le décompte d’utilisation maximale pour le sémaphore. Doit être supérieure à 0.  
  
 *pstrName*  
 Le nom du sémaphore. Doit être fourni si le sémaphore est accessible au-delà des limites de processus. Si `NULL`, l’objet sera sans nom. Si le nom correspond à un sémaphore existant, le constructeur crée quand même un `CSemaphore` objet qui référence le sémaphore de ce nom. Si le nom correspond à un objet de synchronisation existant qui n’est pas un sémaphore, la construction échoue.  
  
 *lpsaAttributes*  
 Attributs de sécurité de l’objet de sémaphore. Pour obtenir une description complète de cette structure, consultez [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) dans le SDK Windows.  
  
### <a name="remarks"></a>Notes  
 Pour accéder à ou libérer un `CSemaphore` d’objet, de créer un [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) objet et appelez ses [verrou](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) fonctions membres.  
  
> [!IMPORTANT]
>  Après avoir créé le `CSemaphore` de l’objet, utilisez [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) pour vous assurer que le mutex n’existait pas. Si le mutex n’existait inattendu, cela peut indiquer un processus non fiable est l’occupation et peut être ayant l’intention d’utiliser le mutex à des fins malveillantes. Dans ce cas, la procédure en termes de sécurité recommandée consiste à fermer le handle et continuer comme si une défaillance s’est produite lors de la création de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [CSyncObject, classe](../../mfc/reference/csyncobject-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)



