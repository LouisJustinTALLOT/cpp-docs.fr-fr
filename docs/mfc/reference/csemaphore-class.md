---
title: CSemaphore, classe
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: 26e1fd55d321b221f4732874d57d02a79c4c6398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318503"
---
# <a name="csemaphore-class"></a>CSemaphore, classe

Un objet `CSemaphore` de classe représente un « sémaphore » — un objet de synchronisation qui permet à un nombre limité de threads dans un ou plusieurs processus d’accéder à un maintient un nombre de threads qui accèdent actuellement à une ressource spécifiée.

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

Les sémaphores sont utiles pour contrôler l’accès à une ressource partagée qui ne peut prendre en charge qu’un nombre limité d’utilisateurs. Le nombre actuel `CSemaphore` de l’objet est le nombre d’utilisateurs supplémentaires autorisés. Lorsque le nombre atteint zéro, toutes les tentatives d’utiliser la ressource contrôlée par l’objet `CSemaphore` seront insérées dans une file d’attente du système et attendre jusqu’à ce qu’ils soit temps ou le nombre s’élève au-dessus de 0. Le nombre maximum d’utilisateurs qui peuvent accéder à la ressource `CSemaphore` contrôlée en même temps est spécifié lors de la construction de l’objet.

Pour utiliser `CSemaphore` un objet, construisez l’objet `CSemaphore` en cas de besoin. Spécifiez le nom du sémaphore que vous souhaitez attendre, et que votre application doit d’abord en être propriétaire. Vous pouvez ensuite accéder au sémaphore lorsque le constructeur revient. Appelez [CSyncObject: :Déverrouiller](../../mfc/reference/csyncobject-class.md#unlock) lorsque vous avez terminé d’accéder à la ressource contrôlée.

Une autre méthode `CSemaphore` pour l’utilisation d’objets consiste à ajouter une variable de type `CSemaphore` en tant que membre des données à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlé, `CSemaphore` appelez le constructeur du membre des données en spécifiant le nombre d’accès initial, le nombre d’accès maximal, le nom du sémaphore (s’il est utilisé au-delà des limites du processus) et les attributs de sécurité souhaités.

Pour accéder aux `CSemaphore` ressources contrôlées par des objets de cette manière, créez d’abord une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou [de type CMultiLock](../../mfc/reference/cmultilock-class.md) dans la fonction de membre d’accès de votre ressource. Appelez ensuite la fonction `Lock` de membre de l’objet de verrouillage (par exemple, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). À ce stade, votre thread aura soit accès à la ressource, attendre que la ressource soit libérée et y accéder, ou attendre que la ressource soit libérée et le temps d’absence, à défaut d’accéder à la ressource. Dans tous les cas, votre ressource a été consultée d’une manière sans fil. Pour libérer la ressource, utilisez `Unlock` la fonction de membre de l’objet de verrouillage (par exemple, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), ou laissez l’objet de verrouillage tomber hors de portée.

Alternativement, vous pouvez `CSemaphore` créer un objet autonome, et y accéder explicitement avant de tenter d’accéder à la ressource contrôlée. Cette méthode, bien que plus claire pour quelqu’un qui lit votre code source, est plus sujette à l’erreur.

Pour plus d’informations `CSemaphore` sur la façon d’utiliser des objets, voir l’article [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Spécifications

**En-tête:** afxmt.h

## <a name="csemaphorecsemaphore"></a><a name="csemaphore"></a>CSemaphore::CSemaphore

Construit un objet nommé `CSemaphore` ou anonyme.

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Paramètres

*lInitialCount (en)*<br/>
L’utilisation initiale compte pour le sémaphore. Doit être supérieur ou égal à 0, et moins ou égal à *lMaxCount*.

*lMaxCount (en)*<br/>
Le nombre maximum d’utilisation pour le sémaphore. Doit être supérieure à 0.

*pstrName (en)*<br/>
Le nom du sémaphore. Doit être fourni si le sémaphore sera accessible au-delà des limites du processus. Si `NULL`, l’objet sera sans nom. Si le nom correspond à un sémaphore `CSemaphore` existant, le constructeur construit un nouvel objet qui fait référence au sémaphore de ce nom. Si le nom correspond à un objet de synchronisation existant qui n’est pas un sémaphore, la construction échouera.

*lpsaAttributes*<br/>
Attributs de sécurité pour l’objet sémaphore. Pour une description complète de cette structure, voir [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) dans le SDK Windows.

### <a name="remarks"></a>Notes

Pour accéder ou `CSemaphore` libérer un objet, créez un objet [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) et appelez ses fonctions de membre [Lock](../../mfc/reference/csinglelock-class.md#lock) and [Unlock.](../../mfc/reference/csinglelock-class.md#unlock)

> [!IMPORTANT]
> Après avoir `CSemaphore` créé l’objet, utilisez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour vous assurer que le mutex n’existe pas déjà. Si le mutex a existé de façon inattendue, il peut indiquer un processus voyous est accroupi et peut-être l’intention d’utiliser le mutex malicieusement. Dans ce cas, la procédure recommandée de sécurité est de fermer la poignée et de continuer comme s’il y avait un échec dans la création de l’objet.

## <a name="see-also"></a>Voir aussi

[Classe CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
