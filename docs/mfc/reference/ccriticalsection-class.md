---
title: CCriticalSection, classe
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
ms.openlocfilehash: d79199a332f6930619e6b4995b04bc590b6ea580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369365"
---
# <a name="ccriticalsection-class"></a>CCriticalSection, classe

Représente une « section critique » — un objet de synchronisation qui permet à un thread à la fois d’accéder à une ressource ou à une section de code.

## <a name="syntax"></a>Syntaxe

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CCriticalSection::CCriticalSection](#ccriticalsection)|Construit un objet `CCriticalSection`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CCriticalSection::Lock](#lock)|Utiliser pour accéder `CCriticalSection` à l’objet.|
|[CCriticalSection::Unlock](#unlock)|Libère l'objet `CCriticalSection`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CCriticalSection::opérateur CRITICAL_SECTION](#operator_critical_section_star)|Récupère un pointeur sur l’objet CRITICAL_SECTION interne.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCriticalSection::m_sect](#m_sect)|Un objet CRITICAL_SECTION.|

## <a name="remarks"></a>Notes

Les sections critiques sont utiles lorsqu’un seul thread à la fois peut être autorisé à modifier des données ou une autre ressource contrôlée. Par exemple, l’ajout de nœuds à une liste liée est un processus qui ne devrait être autorisé que par un thread à la fois. En utilisant `CCriticalSection` un objet pour contrôler la liste liée, un seul thread à la fois peut accéder à la liste.

> [!NOTE]
> La fonctionnalité de `CCriticalSection` la classe est fournie par un objet réel Win32 CRITICAL_SECTION.

Les sections critiques sont utilisées au lieu de mutexes (voir [CMutex](../../mfc/reference/cmutex-class.md)) lorsque la vitesse est critique et que la ressource ne sera pas utilisée au-delà des limites du processus.

Il existe deux méthodes `CCriticalSection` pour l’utilisation d’un objet : autonome et intégré dans une classe.

- Méthode autonome Pour utiliser un `CCriticalSection` objet autonome, `CCriticalSection` construisez l’objet en cas de besoin. Après un retour réussi du constructeur, verrouillez explicitement l’objet avec un appel à [l’écluse](#lock). Appelez [déverrouiller](#unlock) lorsque vous avez terminé d’accéder à la section critique. Cette méthode, bien que plus claire pour quelqu’un qui lit votre code source, est plus sujette à l’erreur que vous devez vous rappeler de verrouiller et déverrouiller la section critique avant et après l’accès.

   Une méthode plus préférable est d’utiliser la classe [CSingleLock.](../../mfc/reference/csinglelock-class.md) Il a `Lock` également `Unlock` une méthode et, mais vous n’avez pas à vous soucier de débloquer la ressource si une exception se produit.

- Méthode intégrée Vous pouvez également partager une classe `CCriticalSection`avec plusieurs threads en ajoutant un membre de données de type à la classe et en verrouillant le membre de données en cas de besoin.

Pour plus d’informations sur l’utilisation d’objets, `CCriticalSection` voir l’article [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>Spécifications

**En-tête:** afxmt.h

## <a name="ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a>CCriticalSection::CCriticalSection

Construit un objet `CCriticalSection`.

```
CCriticalSection();
```

### <a name="remarks"></a>Notes

Pour accéder ou `CCriticalSection` libérer un objet, créez un objet [CSingleLock](../../mfc/reference/csinglelock-class.md) et appelez ses fonctions de membre [Lock](../../mfc/reference/csinglelock-class.md#lock) and [Unlock.](../../mfc/reference/csinglelock-class.md#unlock) Si `CCriticalSection` l’objet est utilisé autonome, appelez sa fonction de membre [Unlock](#unlock) pour le libérer.

Si le constructeur ne parvient pas à allouer la mémoire du système requise, une exception de mémoire (de type [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) est automatiquement lancée.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CCriticalSection::Lock](#lock).

## <a name="ccriticalsectionlock"></a><a name="lock"></a>CCriticalSection::Lock

Appelez cette fonction de membre pour accéder à l’objet de section critique.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>Paramètres

*dwTimeout*<br/>
`Lock`ignore cette valeur de paramètre.

### <a name="return-value"></a>Valeur de retour

Nonzero si la fonction a été réussie; sinon 0.

### <a name="remarks"></a>Notes

`Lock`est un appel de blocage qui ne reviendra pas jusqu’à ce que l’objet de section critique soit signalé (devient disponible).

Si des attentes chronométrées sont nécessaires, vous pouvez `CCriticalSection` utiliser un objet [CMutex](../../mfc/reference/cmutex-class.md) au lieu d’un objet.

Si `Lock` vous ne parussez pas la mémoire du système nécessaire, une exception de mémoire (de type [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) est automatiquement lancée.

### <a name="example"></a>Exemple

Cet exemple montre l’approche de section critique imbriquée `_strShared` en contrôlant `CCriticalSection` l’accès à une ressource partagée (l’objet statique) à l’aide d’un objet partagé. La `SomeMethod` fonction démontre la mise à jour d’une ressource partagée d’une manière sûre.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

## <a name="ccriticalsectionm_sect"></a><a name="m_sect"></a>CCriticalSection::m_sect

Contient un objet de section `CCriticalSection` critique qui est utilisé par toutes les méthodes.

```
CRITICAL_SECTION m_sect;
```

## <a name="ccriticalsectionoperator-critical_section"></a><a name="operator_critical_section_star"></a>CCriticalSection::opérateur CRITICAL_SECTION

Récupère un objet CRITICAL_SECTION.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer un pointeur sur l’objet CRITICAL_SECTION interne.

## <a name="ccriticalsectionunlock"></a><a name="unlock"></a>CCriticalSection::Unlock

Libère `CCriticalSection` l’objet pour une autre utilisation par un autre thread.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `CCriticalSection` l’objet était la propriété du fil et la libération a été réussie; sinon 0.

### <a name="remarks"></a>Notes

Si `CCriticalSection` l’utilisation est autonome, `Unlock` doit être appelée immédiatement après avoir terminé l’utilisation de la ressource contrôlée par la section critique. Si un objet [CSingleLock](../../mfc/reference/csinglelock-class.md) `CCriticalSection::Unlock` est utilisé, sera appelé `Unlock` par la fonction membre de l’objet de verrouillage.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CCriticalSection::Lock](#lock).

## <a name="see-also"></a>Voir aussi

[Classe CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMutex, classe](../../mfc/reference/cmutex-class.md)
