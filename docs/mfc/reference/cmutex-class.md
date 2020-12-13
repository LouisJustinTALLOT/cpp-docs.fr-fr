---
description: 'En savoir plus sur : classe CMutex'
title: CMutex, classe
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: 4890a99d52fb8142bac0cc25d6a23ef6dbcaed5b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331491"
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

Les mutex sont utiles lorsqu’un seul thread à la fois peut être autorisé à modifier des données ou d’autres ressources contrôlées. Par exemple, l’ajout de nœuds à une liste liée est un processus qui ne doit être autorisé que par un seul thread à la fois. En utilisant un `CMutex` objet pour contrôler la liste liée, un seul thread à la fois peut accéder à la liste.

Pour utiliser un `CMutex` objet, construisez l' `CMutex` objet quand il est nécessaire. Spécifiez le nom du mutex que vous souhaitez attendre, et que votre application doit initialement la posséder. Vous pouvez ensuite accéder au mutex lorsque le constructeur retourne. Appelez [CSyncObject :: Unlock](../../mfc/reference/csyncobject-class.md#unlock) lorsque vous avez terminé d’accéder à la ressource contrôlée.

Une autre méthode pour l’utilisation d' `CMutex` objets consiste à ajouter une variable de type `CMutex` comme donnée membre à la classe que vous souhaitez contrôler. Pendant la construction de l’objet contrôlé, appelez le constructeur du `CMutex` membre de données en spécifiant si le mutex est initialement détenu, le nom du mutex (s’il sera utilisé au-delà des limites du processus) et les attributs de sécurité souhaités.

Pour accéder aux ressources contrôlées par `CMutex` les objets de cette manière, commencez par créer une variable de type [CSingleLock](../../mfc/reference/csinglelock-class.md) ou [CMultiLock](../../mfc/reference/cmultilock-class.md) dans la fonction membre Access de votre ressource. Appelez ensuite la fonction membre de l’objet lock `Lock` (par exemple, [CSingleLock :: Lock](../../mfc/reference/csinglelock-class.md#lock)). À ce stade, votre thread peut accéder à la ressource, attendre que la ressource soit libérée et y accéder, ou attendre la libération et l’expiration de la ressource, ce qui ne peut pas accéder à la ressource. Dans tous les cas, votre ressource est accessible de manière thread-safe. Pour libérer la ressource, utilisez la fonction membre de l’objet lock `Unlock` (par exemple, [CSingleLock :: Unlock](../../mfc/reference/csinglelock-class.md#unlock)), ou autorisez l’objet Lock à tomber hors de portée.

Pour plus d’informations sur l’utilisation des `CMutex` objets, consultez l’article [Multithreading : comment utiliser les classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>Spécifications

**En-tête :** afxmt. h

## <a name="cmutexcmutex"></a><a name="cmutex"></a> CMutex::CMutex

Construit un objet nommé ou sans nom `CMutex` .

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Paramètres

*bInitiallyOwn*<br/>
Spécifie si le thread `CMutex` qui crée initialement l’objet a accès à la ressource contrôlée par le mutex.

*lpszName*<br/>
Nom de l'objet `CMutex`. Si un autre mutex portant le même nom existe, *lpszName* doit être fourni si l’objet sera utilisé au-delà des limites du processus. Si la **valeur est null**, le mutex ne sera pas nommé. Si le nom correspond à un mutex existant, le constructeur génère un nouvel `CMutex` objet qui fait référence au mutex de ce nom. Si le nom correspond à un objet de synchronisation existant qui n’est pas un mutex, la construction échoue.

*lpsaAttribute*<br/>
Attributs de sécurité pour l’objet Mutex. Pour obtenir une description complète de cette structure, consultez [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) dans le SDK Windows.

### <a name="remarks"></a>Notes

Pour accéder ou libérer un `CMutex` objet, créez un objet [CMultiLock](../../mfc/reference/cmultilock-class.md) ou [CSingleLock](../../mfc/reference/csinglelock-class.md) et appelez ses fonctions membres [Lock](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) . Si l' `CMutex` objet est utilisé de manière autonome, appelez sa `Unlock` fonction membre pour le libérer.

> [!IMPORTANT]
> Après avoir créé l' `CMutex` objet, utilisez [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) pour vous assurer que le mutex n’existait pas déjà. Si le mutex s’est exécuté de façon inattendue, cela peut indiquer qu’un processus non autorisé est une opération d’occupation et peut être l’intention d’utiliser le mutex à des fins malveillantes. Dans ce cas, la procédure recommandée pour la sécurité consiste à fermer le descripteur et à continuer comme en cas de défaillance lors de la création de l’objet.

## <a name="see-also"></a>Voir aussi

[CSyncObject, classe](../../mfc/reference/csyncobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
