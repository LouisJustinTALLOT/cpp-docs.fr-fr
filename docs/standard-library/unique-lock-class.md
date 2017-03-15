---
title: unique_lock, classe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::unique_lock
dev_langs:
- C++
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 27145bb5aab7087ddf9dd7d56d51f242062268ff
ms.lasthandoff: 02/24/2017

---
# <a name="uniquelock-class"></a>unique_lock, classe
Représente un modèle qui peut être instancié pour créer des objets qui gèrent le verrouillage et le déverrouillage d'un `mutex`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Mutex>
class unique_lock;
```  
  
## <a name="remarks"></a>Notes  
 L’argument de modèle `Mutex` doit nommer un *type mutex*.  
  
 En interne, un `unique_lock` stocke un pointeur vers un objet `mutex` associé et un `bool` qui indique si le thread actuel détient le `mutex`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`mutex_type`|Synonyme de l’argument de modèle `Mutex`.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[unique_lock, constructeur](#unique_lock__unique_lock_constructor)|Construit un objet `unique_lock`.|  
|[~unique_lock, destructeur](#unique_lock___dtorunique_lock_destructor)|Libère toutes les ressources associées à l’objet `unique_lock`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[lock](#unique_lock__lock_method)|Bloque le thread appelant jusqu’à ce que le thread obtienne la propriété du `mutex` associé.|  
|[mutex](#unique_lock__mutex_method)|Récupère le pointeur stocké vers le `mutex` associé.|  
|[owns_lock](#unique_lock__owns_lock_method)|Spécifie si le thread appelant possède le `mutex` associé.|  
|[release](#unique_lock__release_method)|Dissocie l’objet `unique_lock` de l’objet `mutex` associé.|  
|[swap](#unique_lock__swap_method)|Échange le `mutex` associé et l’état de propriété avec ceux d’un objet spécifié.|  
|[try_lock](#unique_lock__try_lock_method)|Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.|  
|[try_lock_for](#unique_lock__try_lock_for_method)|Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.|  
|[try_lock_until](#unique_lock__try_lock_until_method)|Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.|  
|[unlock](#unique_lock__unlock_method)|Libère la propriété du `mutex` associé.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[operator bool](#unique_lock__operator_bool)|Spécifie si le thread appelant possède le `mutex` associé.|  
|[operator=](#unique_lock__operator_eq)|Copie le pointeur `mutex` stocké et l’état de propriété associé à partir d’un objet spécifié.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage  
 `unique_lock`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** mutex  
  
 **Espace de noms :** std  
  
##  <a name="a-nameuniquelocklockmethoda--lock"></a><a name="unique_lock__lock_method"></a>  lock  
 Bloque le thread appelant jusqu’à ce que le thread obtienne la propriété du `mutex` associé.  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>Notes  
 Si le pointeur `mutex` stocké est `null`, cette méthode lève une [system_error](../standard-library/system-error-class.md) avec le code d’erreur `operation_not_permitted`.  
  
 Si le thread appelant possède déjà le `mutex` associé, cette méthode lève une `system_error` avec le code d’erreur `resource_deadlock_would_occur`.  
  
 Sinon, cette méthode appelle `lock` sur le `mutex` associé et définit l’indicateur de propriété de thread interne sur `true`.  
  
##  <a name="a-nameuniquelockmutexmethoda--mutex"></a><a name="unique_lock__mutex_method"></a>  mutex  
 Récupère le pointeur stocké vers le `mutex` associé.  
  
```cpp  
mutex_type *mutex() const noexcept;
```  
  
##  <a name="a-nameuniquelockoperatorboola--operator-bool"></a><a name="unique_lock__operator_bool"></a>  operator bool  
 Spécifie si le thread appelant possède le mutex associé.  
  
```cpp  
explicit operator bool() noexcept
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si le thread possède le mutex ; sinon, `false`.  
  
##  <a name="a-nameuniquelockoperatoreqa--operator"></a><a name="unique_lock__operator_eq"></a>  operator=  
 Copie le pointeur `mutex` stocké et l’état de propriété associé à partir d’un objet spécifié.  
  
```cpp  
unique_lock& operator=(unique_lock&& Other) noexcept;
```  
  
### <a name="parameters"></a>Paramètres  
 `Other`  
 Objet `unique_lock`.  
  
### <a name="return-value"></a>Valeur de retour  
 `*this`  
  
### <a name="remarks"></a>Notes  
 Si le thread appelant possède le `mutex` précédemment associé, avant que cette méthode appelle `unlock` sur le `mutex`, il assigne les nouvelles valeurs.  
  
 Après la copie, cette méthode définit `Other` à un état construit par défaut.  
  
##  <a name="a-nameuniquelockownslockmethoda--ownslock"></a><a name="unique_lock__owns_lock_method"></a>  owns_lock  
 Spécifie si le thread appelant possède le `mutex` associé.  
  
```cpp  
bool owns_lock() const noexcept;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si le thread possède le `mutex` ; sinon, `false`.  
  
##  <a name="a-nameuniquelockreleasemethoda--release"></a><a name="unique_lock__release_method"></a>  release  
 Dissocie l’objet `unique_lock` de l’objet `mutex` associé.  
  
```cpp  
mutex_type *release() noexcept;
```  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur précédente du pointeur `mutex` stocké.  
  
### <a name="remarks"></a>Notes  
 Cette méthode définit la valeur du pointeur `mutex` stocké à 0 et l’indicateur de propriété `mutex` interne à `false`.  
  
##  <a name="a-nameuniquelockswapmethoda--swap"></a><a name="unique_lock__swap_method"></a>  swap  
 Échange le `mutex` associé et l’état de propriété avec ceux d’un objet spécifié.  
  
```
void swap(unique_lock& Other) noexcept;
```  
  
### <a name="parameters"></a>Paramètres  
 `Other`  
 Objet `unique_lock`.  
  
##  <a name="a-nameuniquelocktrylockmethoda--trylock"></a><a name="unique_lock__try_lock_method"></a>  try_lock  
 Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.  
  
```cpp  
bool try_lock() noexcept;
```  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si la méthode obtient correctement la propriété du `mutex` ; sinon, `false`.  
  
### <a name="remarks"></a>Notes  
 Si le pointeur `mutex` stocké est `null`, la méthode lève une [system_error](../standard-library/system-error-class.md) avec le code d’erreur `operation_not_permitted`.  
  
 Si le thread appelant possède déjà le `mutex`, la méthode lève une `system_error` avec le code d’erreur `resource_deadlock_would_occur`.  
  
##  <a name="a-nameuniquelocktrylockformethoda--trylockfor"></a><a name="unique_lock__try_lock_for_method"></a>  try_lock_for  
 Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.  
  
```
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```  
  
### <a name="parameters"></a>Paramètres  
 `Rel_time`  
 Objet [chrono::duration](../standard-library/duration-class.md) qui spécifie la durée maximale pendant laquelle la méthode essaie d’obtenir la propriété du `mutex`.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si la méthode obtient correctement la propriété du `mutex` ; sinon, `false`.  
  
### <a name="remarks"></a>Notes  
 Si le pointeur `mutex` stocké est `null`, la méthode lève une [system_error](../standard-library/system-error-class.md) avec le code d’erreur `operation_not_permitted`.  
  
 Si le thread appelant possède déjà le `mutex`, la méthode lève une `system_error` avec le code d’erreur `resource_deadlock_would_occur`.  
  
##  <a name="a-nameuniquelocktrylockuntilmethoda--trylockuntil"></a><a name="unique_lock__try_lock_until_method"></a>  try_lock_until  
 Tente d'obtenir la propriété de la référence `mutex` associée sans se bloquer.  
  
```cpp  
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```  
  
### <a name="parameters"></a>Paramètres  
 `Abs_time`  
 Point dans le temps qui spécifie le seuil au-delà duquel la méthode ne tente plus d'obtenir la propriété du `mutex`.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` si la méthode obtient correctement la propriété du `mutex` ; sinon, `false`.  
  
### <a name="remarks"></a>Notes  
 Si le pointeur `mutex` stocké est `null`, la méthode lève une [system_error](../standard-library/system-error-class.md) avec le code d’erreur `operation_not_permitted`.  
  
 Si le thread appelant possède déjà le `mutex`, la méthode lève une `system_error` avec le code d’erreur `resource_deadlock_would_occur`.  
  
##  <a name="a-nameuniquelockuniquelockconstructora--uniquelock-constructor"></a><a name="unique_lock__unique_lock_constructor"></a>  unique_lock, constructeur  
 Construit un objet `unique_lock`.  
  
```cpp  
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>  
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>  
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```  
  
### <a name="parameters"></a>Paramètres  
 `Mtx`  
 Objet de type mutex.  
  
 `Rel_time`  
 Objet [chrono::duration](../standard-library/duration-class.md) qui spécifie la durée maximale pendant laquelle la méthode essaie d’obtenir la propriété du `mutex`.  
  
 `Abs_time`  
 Point dans le temps qui spécifie le seuil au-delà duquel la méthode ne tente plus d'obtenir la propriété du `mutex`.  
  
 `Other`  
 Objet `unique_lock`.  
  
### <a name="remarks"></a>Notes  
 Le premier constructeur construit un objet qui a une valeur de pointeur mutex associé de 0.  
  
 Le deuxième constructeur déplace l’état mutex associé de `Other`. Après le déplacement, `Other` n’est plus associé à un mutex.  
  
 Les constructeurs restants stockent & `Mtx` en tant que pointeur `mutex` stocké. L’appartenance du `mutex` est déterminée par le deuxième argument, s’il existe.  
  
|||  
|-|-|  
|`No argument`|L’appartenance est obtenue en appelant la méthode `lock` sur l’objet `mutex` associé.|  
|`Adopt`|L’appartenance est supposée. `Mtx` doit être verrouillé quand le constructeur est appelé.|  
|`Defer`|Le thread appelant est supposé ne pas posséder l’objet `mutex`. `Mtx` ne doit pas être verrouillé quand le constructeur est appelé.|  
|`Try`|L’appartenance est déterminée en appelant `try_lock` sur l’objet `mutex` associé. Le constructeur ne lève aucune exception.|  
|`Rel_time`|L’appartenance est déterminée en appelant `try_lock_for(Rel_time)`.|  
|`Abs_time`|L’appartenance est déterminée en appelant `try_lock_until(Abs_time)`.|  
  
##  <a name="a-nameuniquelockdtoruniquelockdestructora--uniquelock-destructor"></a><a name="unique_lock___dtorunique_lock_destructor"></a>  ~unique_lock, destructeur  
 Libère toutes les ressources associées à l’objet `unique_lock`.  
  
```cpp  
~unique_lock() noexcept;
```  
  
### <a name="remarks"></a>Notes  
 Si le thread appelant possède le `mutex` associé, le destructeur libère la propriété en appelant unlock sur l’objet `mutex`.  
  
##  <a name="a-nameuniquelockunlockmethoda--unlock"></a><a name="unique_lock__unlock_method"></a>  unlock  
 Libère la propriété du `mutex` associé.  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>Notes  
 Si le thread appelant ne possède pas le `mutex` associé, cette méthode lève une [system_error](../standard-library/system-error-class.md) avec le code d’erreur `operation_not_permitted`.  
  
 Sinon, cette méthode appelle `unlock` sur le `mutex` associé et définit l’indicateur de propriété de thread interne sur `false`.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)




