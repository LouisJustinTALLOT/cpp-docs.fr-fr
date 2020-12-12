---
description: 'En savoir plus sur : CSemaphore, classe'
title: CSemaphore (classe)
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: 102b7ac9d7f934e3a04783c9ab537a858541c780
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264698"
---
# <a name="csemaphore-class"></a>CSemaphore (classe)

Un objet de classe `CSemaphore` représente un « sémaphore », c’est-à-dire un objet de synchronisation qui permet à un nombre limité de threads dans un ou plusieurs processus d’accéder à un, gère le nombre de threads qui accèdent actuellement à une ressource spécifiée.

## <a name="syntax"></a>Syntaxe

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSemaphore :: CSemaphore](#csemaphore)|Construit un objet `CSemaphore`.|

## <a name="remarks"></a>Notes

Les sémaphores sont utiles pour contrôler l’accès à une ressource partagée qui ne peut prendre en charge qu’un nombre limité d’utilisateurs. Le nombre actuel de l' `CSemaphore` objet est le nombre d’utilisateurs supplémentaires autorisés. Lorsque le nombre atteint zéro, toutes les tentatives d’utilisation de la ressource contrôlée par l' `CSemaphore` objet sont insérées dans une file d’attente système et patientent jusqu’à expiration ou que le nombre dépasse 0. Le nombre maximal d’utilisateurs pouvant accéder à la ressource contrôlée à un moment donné est spécifié lors de la construction de l' `CSemaphore` objet.

Pour utiliser un `CSemaphore` objet, construisez l' `CSemaphore` objet quand il est nécessaire. Spécifiez le nom du sémaphore sur lequel vous souhaitez attendre, et que votre application doit initialement la posséder. Vous pouvez ensuite accéder au sémaphore lorsque le constructeur retourne. Appelez [CSyncObject :: Unlock](../../mfc/reference/csyncobject-class.md#unlock) lorsque vous avez terminé d’accéder à la ressource contrôlée.

Une autre méthode pour l’utilisation d' `CSemaphore` objets consiste à ajouter une variable de type `CSemaphore` comme donnée membre à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlé, appelez le constructeur du `CSemaphore` membre de données en spécifiant le nombre d’accès initial, le nombre maximal d’accès, le nom du sémaphore (s’il sera utilisé au-delà des limites du processus) et les attributs de sécurité souhaités.

Pour accéder aux ressources contrôlées par `CSemaphore` les objets de cette manière, commencez par créer une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou [CMultiLock](../../mfc/reference/cmultilock-class.md) dans la fonction membre Access de votre ressource. Appelez ensuite la fonction membre de l’objet lock `Lock` (par exemple, [CSingleLock :: Lock](../../mfc/reference/csinglelock-class.md#lock)). À ce stade, votre thread peut accéder à la ressource, attendre que la ressource soit libérée et y accéder, ou attendre la libération et l’expiration de la ressource, ce qui ne peut pas accéder à la ressource. Dans tous les cas, votre ressource est accessible de manière thread-safe. Pour libérer la ressource, utilisez la fonction membre de l’objet lock `Unlock` (par exemple, [CSingleLock :: Unlock](../../mfc/reference/csinglelock-class.md#unlock)), ou autorisez l’objet Lock à tomber hors de portée.

Vous pouvez également créer un `CSemaphore` objet autonome et y accéder explicitement avant de tenter d’accéder à la ressource contrôlée. Cette méthode, bien que plus claire à la lecture de votre code source, est plus sujette à une erreur.

Pour plus d’informations sur l’utilisation des `CSemaphore` objets, consultez l’article [Multithreading : comment utiliser les classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Spécifications

**En-tête :** afxmt. h

## <a name="csemaphorecsemaphore"></a><a name="csemaphore"></a> CSemaphore :: CSemaphore

Construit un objet nommé ou sans nom `CSemaphore` .

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Paramètres

*lInitialCount*<br/>
Le nombre initial d’utilisations du sémaphore. Doit être supérieur ou égal à 0 et inférieur ou égal à *lMaxCount*.

*lMaxCount*<br/>
Nombre maximal d’utilisations du sémaphore. Doit être supérieure à 0.

*pstrName*<br/>
Nom du sémaphore. Doit être fourni si le sémaphore est accessible à travers les limites du processus. Si `NULL` la condition est, l’objet ne sera pas nommé. Si le nom correspond à un sémaphore existant, le constructeur génère un nouvel `CSemaphore` objet qui fait référence au sémaphore de ce nom. Si le nom correspond à un objet de synchronisation existant qui n’est pas un sémaphore, la construction échoue.

*lpsaAttributes*<br/>
Attributs de sécurité pour l’objet Semaphore. Pour obtenir une description complète de cette structure, consultez [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) dans le SDK Windows.

### <a name="remarks"></a>Notes

Pour accéder ou libérer un `CSemaphore` objet, créez un objet [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) et appelez ses fonctions membres [Lock](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) .

> [!IMPORTANT]
> Après avoir créé l' `CSemaphore` objet, utilisez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour vous assurer que le mutex n’existait pas déjà. Si le mutex s’est exécuté de façon inattendue, cela peut indiquer qu’un processus non autorisé est une opération d’occupation et peut être l’intention d’utiliser le mutex à des fins malveillantes. Dans ce cas, la procédure recommandée pour la sécurité consiste à fermer le descripteur et à continuer comme en cas de défaillance lors de la création de l’objet.

## <a name="see-also"></a>Voir aussi

[CSyncObject, classe](../../mfc/reference/csyncobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
