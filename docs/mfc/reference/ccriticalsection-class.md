---
description: 'En savoir plus sur : CCriticalSection, classe'
title: CCriticalSection (classe)
ms.date: 11/04/2016
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
ms.openlocfilehash: 0041eea4453ec02159b26805bd5e7a264a410504
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227791"
---
# <a name="ccriticalsection-class"></a>CCriticalSection (classe)

Représente une « section critique », un objet de synchronisation qui permet à un thread à la fois d’accéder à une ressource ou à une section de code.

## <a name="syntax"></a>Syntaxe

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCriticalSection :: CCriticalSection](#ccriticalsection)|Construit un objet `CCriticalSection`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCriticalSection :: Lock](#lock)|Utilisez pour accéder à l' `CCriticalSection` objet.|
|[CCriticalSection :: Unlock](#unlock)|Libère l'objet `CCriticalSection`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CCriticalSection :: Operator CRITICAL_SECTION *](#operator_critical_section_star)|Récupère un pointeur vers l’objet CRITICAL_SECTION interne.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCriticalSection :: m_sect](#m_sect)|Objet CRITICAL_SECTION.|

## <a name="remarks"></a>Notes

Les sections critiques sont utiles lorsqu’un seul thread à la fois peut être autorisé à modifier des données ou d’autres ressources contrôlées. Par exemple, l’ajout de nœuds à une liste liée est un processus qui ne doit être autorisé que par un seul thread à la fois. En utilisant un `CCriticalSection` objet pour contrôler la liste liée, un seul thread à la fois peut accéder à la liste.

> [!NOTE]
> Les fonctionnalités de la `CCriticalSection` classe sont fournies par un objet critical_section Win32 réel.

Les sections critiques sont utilisées à la place des mutex (consultez [CMutex](../../mfc/reference/cmutex-class.md)) lorsque la vitesse est critique et que la ressource n’est pas utilisée au-delà des limites du processus.

Il existe deux méthodes pour utiliser un `CCriticalSection` objet : autonome et incorporé dans une classe.

- Méthode autonome pour utiliser un `CCriticalSection` objet autonome, construisez l' `CCriticalSection` objet quand cela est nécessaire. Après un retour réussi du constructeur, verrouillez explicitement l’objet avec un appel à [Lock](#lock). Appelez [Unlock](#unlock) lorsque vous avez terminé d’accéder à la section critique. Cette méthode, bien que plus claire à la lecture de votre code source, est plus sujette à une erreur, car vous devez penser à verrouiller et déverrouiller la section critique avant et après l’accès.

   Une méthode plus préférable consiste à utiliser la classe [CSingleLock](../../mfc/reference/csinglelock-class.md) . Elle a également une `Lock` `Unlock` méthode et, mais vous n’avez pas à vous soucier du déverrouillage de la ressource si une exception se produit.

- Méthode incorporée vous pouvez également partager une classe avec plusieurs threads en ajoutant un `CCriticalSection` membre de données de type à la classe et en verrouillant le membre de données si nécessaire.

Pour plus d’informations sur l’utilisation des `CCriticalSection` objets, consultez l’article [Multithreading : comment utiliser les classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>Spécifications

**En-tête :** afxmt. h

## <a name="ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a> CCriticalSection :: CCriticalSection

Construit un objet `CCriticalSection`.

```
CCriticalSection();
```

### <a name="remarks"></a>Notes

Pour accéder ou libérer un `CCriticalSection` objet, créez un objet [CSingleLock](../../mfc/reference/csinglelock-class.md) et appelez ses fonctions membres [Lock](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) . Si l' `CCriticalSection` objet est utilisé de manière autonome, appelez sa fonction membre [Unlock](#unlock) pour le libérer.

Si le constructeur ne parvient pas à allouer la mémoire système requise, une exception de mémoire (de type [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) est automatiquement levée.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CCriticalSection :: Lock](#lock).

## <a name="ccriticalsectionlock"></a><a name="lock"></a> CCriticalSection :: Lock

Appelez cette fonction membre pour accéder à l’objet de section critique.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>Paramètres

*dwTimeout*<br/>
`Lock` ignore cette valeur de paramètre.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si la fonction a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

`Lock` est un appel bloquant qui ne retourne pas tant que l’objet de section critique n’est pas signalé (devient disponible).

Si des attentes chronométrées sont nécessaires, vous pouvez utiliser un objet [CMutex](../../mfc/reference/cmutex-class.md) à la place d’un `CCriticalSection` objet.

Si `Lock` ne parvient pas à allouer la mémoire système nécessaire, une exception de mémoire (de type [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) est automatiquement levée.

### <a name="example"></a>Exemple

Cet exemple illustre l’approche de section critique imbriquée en contrôlant l’accès à une ressource partagée (l' `_strShared` objet statique) à l’aide d’un `CCriticalSection` objet partagé. La `SomeMethod` fonction illustre la mise à jour d’une ressource partagée de manière sûre.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

## <a name="ccriticalsectionm_sect"></a><a name="m_sect"></a> CCriticalSection :: m_sect

Contient un objet de section critique qui est utilisé par toutes les `CCriticalSection` méthodes.

```
CRITICAL_SECTION m_sect;
```

## <a name="ccriticalsectionoperator-critical_section"></a><a name="operator_critical_section_star"></a> CCriticalSection :: Operator CRITICAL_SECTION *

Récupère un objet CRITICAL_SECTION.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer un pointeur vers l’objet CRITICAL_SECTION interne.

## <a name="ccriticalsectionunlock"></a><a name="unlock"></a> CCriticalSection :: Unlock

Libère l' `CCriticalSection` objet pour une utilisation par un autre thread.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l' `CCriticalSection` objet était détenu par le thread et si la mise en sortie a réussi ; sinon, 0.

### <a name="remarks"></a>Notes

Si le `CCriticalSection` est utilisé en mode autonome, `Unlock` doit être appelé immédiatement après l’utilisation de la ressource contrôlée par la section critique. Si un objet [CSingleLock](../../mfc/reference/csinglelock-class.md) est utilisé, est `CCriticalSection::Unlock` appelé par la fonction membre de l’objet lock `Unlock` .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CCriticalSection :: Lock](#lock).

## <a name="see-also"></a>Voir aussi

[CSyncObject, classe](../../mfc/reference/csyncobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMutex, classe](../../mfc/reference/cmutex-class.md)
