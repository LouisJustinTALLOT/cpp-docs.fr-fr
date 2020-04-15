---
title: CMutex, classe
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: 2d6f637ab4828b3e70df205ebf359ae45a940d60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363280"
---
# <a name="cmutex-class"></a>CMutex, classe

Représente un "mutex" — un objet de synchronisation qui permet un thread d’accès mutuellement exclusif à une ressource.

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

Les mutexes sont utiles lorsqu’un seul thread à la fois peut être autorisé à modifier des données ou une autre ressource contrôlée. Par exemple, l’ajout de nœuds à une liste liée est un processus qui ne devrait être autorisé que par un thread à la fois. En utilisant `CMutex` un objet pour contrôler la liste liée, un seul thread à la fois peut accéder à la liste.

Pour utiliser `CMutex` un objet, construisez l’objet `CMutex` en cas de besoin. Spécifiez le nom du mutex que vous souhaitez attendre, et que votre application doit d’abord en être propriétaire. Vous pouvez ensuite accéder au mutex lorsque le constructeur revient. Appelez [CSyncObject: :Déverrouiller](../../mfc/reference/csyncobject-class.md#unlock) lorsque vous avez terminé d’accéder à la ressource contrôlée.

Une autre méthode `CMutex` pour l’utilisation d’objets consiste à ajouter une variable de type `CMutex` en tant que membre des données à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlé, `CMutex` appelez le constructeur du membre de données en précisant si le mutex est initialement possédé, le nom du mutex (s’il sera utilisé au-delà des limites du processus), et les attributs de sécurité souhaités.

Pour accéder aux `CMutex` ressources contrôlées par des objets de cette manière, créez d’abord une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou [de type CMultiLock](../../mfc/reference/cmultilock-class.md) dans la fonction de membre d’accès de votre ressource. Appelez ensuite la fonction `Lock` de membre de l’objet de verrouillage (par exemple, [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). À ce stade, votre thread aura soit accès à la ressource, attendre que la ressource soit libérée et y accéder, ou attendre que la ressource soit libérée et le temps d’absence, à défaut d’accéder à la ressource. Dans tous les cas, votre ressource a été consultée d’une manière sans fil. Pour libérer la ressource, utilisez `Unlock` la fonction de membre de l’objet de verrouillage (par exemple, [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), ou laissez l’objet de verrouillage tomber hors de portée.

Pour plus d’informations sur l’utilisation d’objets, `CMutex` voir l’article [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Spécifications

**En-tête:** afxmt.h

## <a name="cmutexcmutex"></a><a name="cmutex"></a>CMutex::CMutex

Construit un objet nommé `CMutex` ou anonyme.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Paramètres

*bInitiallyOwn (en anglais)*<br/>
Précise si le fil `CMutex` créant l’objet a initialement accès à la ressource contrôlée par le mutex.

*lpszName (en)*<br/>
Nom de l'objet `CMutex`. Si un autre mutex du même nom existe, *lpszName* doit être fourni si l’objet sera utilisé au-delà des limites du processus. Si **NULL**, le mutex sera sans nom. Si le nom correspond à un mutex existant, le constructeur construit un nouvel `CMutex` objet qui fait référence au mutex de ce nom. Si le nom correspond à un objet de synchronisation existant qui n’est pas un mutex, la construction échouera.

*lpsaAttribute*<br/>
Attributs de sécurité pour l’objet mutex. Pour une description complète de cette structure, voir [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) dans le SDK Windows.

### <a name="remarks"></a>Notes

Pour accéder ou `CMutex` libérer un objet, créez un objet [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) et appelez ses fonctions de membre [Lock](../../mfc/reference/csinglelock-class.md#lock) and [Unlock.](../../mfc/reference/csinglelock-class.md#unlock) Si `CMutex` l’objet est utilisé autonome, `Unlock` appelez sa fonction de membre pour le libérer.

> [!IMPORTANT]
> Après avoir `CMutex` créé l’objet, utilisez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour vous assurer que le mutex n’existe pas déjà. Si le mutex a existé de façon inattendue, il peut indiquer un processus voyous est accroupi et peut-être l’intention d’utiliser le mutex malicieusement. Dans ce cas, la procédure recommandée de sécurité est de fermer la poignée et de continuer comme s’il y avait un échec dans la création de l’objet.

## <a name="see-also"></a>Voir aussi

[Classe CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
