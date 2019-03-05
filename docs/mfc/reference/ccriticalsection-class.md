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
ms.openlocfilehash: 2c89647afc8a9a8c6564d25afe20d48818a643f2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291039"
---
# <a name="ccriticalsection-class"></a>CCriticalSection, classe

Représente une « section critique », un objet de synchronisation qui permet à un seul thread à la fois pour accéder à une ressource ou une section de code.

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
|[CCriticalSection::Lock](#lock)|Utiliser pour accéder à la `CCriticalSection` objet.|
|[CCriticalSection::Unlock](#unlock)|Libère l'objet `CCriticalSection`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CCriticalSection::operator CRITICAL_SECTION *](#operator_critical_section_star)|Récupère un pointeur vers l’objet CRITICAL_SECTION interne.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CCriticalSection::m_sect](#m_sect)|Un objet CRITICAL_SECTION.|

## <a name="remarks"></a>Notes

Les sections critiques sont utiles lorsque qu’un seul thread à la fois peut être autorisé à modifier des données ou une autre ressource contrôlée. Par exemple, l’ajout de nœuds à une liste liée est un processus qui ne doivent être autorisé par un seul thread à la fois. En utilisant un `CCriticalSection` objet pour contrôler la liste liée, uniquement un seul thread à la fois peut accéder à la liste.

> [!NOTE]
>  Les fonctionnalités de la `CCriticalSection` classe est fournie par un objet Win32 CRITICAL_SECTION réels.

Les sections critiques sont utilisées au lieu de mutex (consultez [CMutex](../../mfc/reference/cmutex-class.md)) lorsque la rapidité est essentielle et la ressource n’utilisera pas les limites du processus.

Il existe deux méthodes pour utiliser un `CCriticalSection` objet : autonome et incorporé dans une classe.

- Méthode autonome à utiliser un autonome `CCriticalSection` d’objet, de construire le `CCriticalSection` de l’objet lorsqu’il est nécessaire. Après un retour réussi à partir du constructeur, verrouiller explicitement l’objet avec un appel à [verrou](#lock). Appelez [Unlock](#unlock) lorsque vous avez terminé l’accès à la section critique. Cette méthode, lors de la façon la plus claire à une personne lisant votre code source, est plus sujette aux erreurs que vous devez penser à verrouiller et déverrouiller la section critique avant et après l’accès.

   Une méthode plus préférable consiste à utiliser le [CSingleLock](../../mfc/reference/csinglelock-class.md) classe. Il possède également un `Lock` et `Unlock` (méthode), mais vous n’avez pas à vous soucier de déverrouillage de la ressource si une exception se produit.

- Incorporé de méthode, vous pouvez également partager une classe avec plusieurs threads en ajoutant un `CCriticalSection`-membre de données de type à la classe et de verrouillage le membre de données si nécessaire.

Pour plus d’informations sur l’utilisation de `CCriticalSection` objets, consultez l’article [Multithreading : Comment utiliser les Classes de synchronisation](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>Spécifications

**En-tête :** afxmt.h

##  <a name="ccriticalsection"></a>  CCriticalSection::CCriticalSection

Construit un objet `CCriticalSection`.

```
CCriticalSection();
```

### <a name="remarks"></a>Notes

Accéder ou de libérer un `CCriticalSection` d’objet, de créer un [CSingleLock](../../mfc/reference/csinglelock-class.md) objet et appelez sa [verrou](../../mfc/reference/csinglelock-class.md#lock) et [Unlock](../../mfc/reference/csinglelock-class.md#unlock) fonctions membres. Si le `CCriticalSection` objet est en cours d’utilisation autonome, appeler ses [Unlock](#unlock) fonction membre pour le libérer.

Si le constructeur ne peut pas allouer la mémoire requise du système, une exception de mémoire (de type [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) est automatiquement levée.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CCriticalSection::Lock](#lock).

##  <a name="lock"></a>  CCriticalSection::Lock

Appelez cette fonction membre pour accéder à l’objet de section critique.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>Paramètres

*dwTimeout*<br/>
`Lock` ignore cette valeur de paramètre.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fonction a réussi ; sinon 0.

### <a name="remarks"></a>Notes

`Lock` est un appel bloquant qui ne retourne pas jusqu'à ce que l’objet de section critique est signalé (devient disponible).

Si les attentes temporisées sont nécessaires, vous pouvez utiliser un [CMutex](../../mfc/reference/cmutex-class.md) de l’objet au lieu d’un `CCriticalSection` objet.

Si `Lock` ne parvient pas à allouer la mémoire système nécessaires, une exception de mémoire (de type [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) est automatiquement levée.

### <a name="example"></a>Exemple

Cet exemple illustre l’approche de section critique imbriquées en contrôlant l’accès à une ressource partagée (statiques `_strShared` objet) à l’aide d’un partage `CCriticalSection` objet. Le `SomeMethod` fonction montre la mise à jour d’une ressource partagée de manière sécurisée.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

##  <a name="m_sect"></a>  CCriticalSection::m_sect

Contient un objet de section critique qui est utilisé par tous les `CCriticalSection` méthodes.

```
CRITICAL_SECTION m_sect;
```

##  <a name="operator_critical_section_star"></a>  CCriticalSection::operator CRITICAL_SECTION *

Récupère un objet CRITICAL_SECTION.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour récupérer un pointeur vers l’objet CRITICAL_SECTION interne.

##  <a name="unlock"></a>  CCriticalSection::Unlock

Versions le `CCriticalSection` objet pour une utilisation par un autre thread.

```
BOOL Unlock();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le `CCriticalSection` objet est détenu par le thread et la version a réussi ; sinon, 0.

### <a name="remarks"></a>Notes

Si le `CCriticalSection` sert autonome, `Unlock` doit être appelée immédiatement après la fin d’utilisation de la ressource contrôlée par la section critique. Si un [CSingleLock](../../mfc/reference/csinglelock-class.md) objet est utilisé, `CCriticalSection::Unlock` sera appelée par l’objet verrou `Unlock` fonction membre.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CCriticalSection::Lock](#lock).

## <a name="see-also"></a>Voir aussi

[CSyncObject, classe](../../mfc/reference/csyncobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CMutex, classe](../../mfc/reference/cmutex-class.md)
