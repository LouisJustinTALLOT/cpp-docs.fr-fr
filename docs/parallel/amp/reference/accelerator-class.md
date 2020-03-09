---
title: accelerator, classe
ms.date: 11/04/2016
f1_keywords:
- AMPRT/accelerator
- AMPRT/Concurrency::accelerator::accelerator
- AMPRT/Concurrency::accelerator::create_view
- AMPRT/Concurrency::accelerator::get_all
- AMPRT/Concurrency::accelerator::get_auto_selection_view
- AMPRT/Concurrency::accelerator::get_dedicated_memory
- AMPRT/Concurrency::accelerator::get_default_cpu_access_type
- AMPRT/Concurrency::accelerator::get_default_view
- AMPRT/Concurrency::accelerator::get_description
- AMPRT/Concurrency::accelerator::get_device_path
- AMPRT/Concurrency::accelerator::get_has_display
- AMPRT/Concurrency::accelerator::get_is_debug
- AMPRT/Concurrency::accelerator::get_is_emulated
- AMPRT/Concurrency::accelerator::get_supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::get_supports_double_precision
- AMPRT/Concurrency::accelerator::get_supports_limited_double_precision
- AMPRT/Concurrency::accelerator::get_version
- AMPRT/Concurrency::accelerator::set_default
- AMPRT/Concurrency::accelerator::set_default_cpu_access_type
- AMPRT/Concurrency::accelerator::cpu_accelerator
- AMPRT/Concurrency::accelerator::dedicated_memory
- AMPRT/Concurrency::accelerator::default_accelerator
- AMPRT/Concurrency::accelerator::default_cpu_access_type
- AMPRT/Concurrency::accelerator::default_view
- AMPRT/Concurrency::accelerator::description
- AMPRT/Concurrency::accelerator::device_path
- AMPRT/Concurrency::accelerator::direct3d_ref
- AMPRT/Concurrency::accelerator::direct3d_warp
- AMPRT/Concurrency::accelerator::has_display
- AMPRT/Concurrency::accelerator::is_debug
- AMPRT/Concurrency::accelerator::is_emulated
- AMPRT/Concurrency::accelerator::supports_cpu_shared_memory
- AMPRT/Concurrency::accelerator::supports_double_precision
- AMPRT/Concurrency::accelerator::supports_limited_double_precision
- AMPRT/Concurrency::accelerator::version
helpviewer_keywords:
- accelerator class
ms.assetid: 37eed593-cf87-4611-9cdc-e98df6c2377a
ms.openlocfilehash: 72a570ab28696730f835c42748a6ea12b865ca55
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855914"
---
# <a name="accelerator-class"></a>accelerator, classe

Un accélérateur est une fonctionnalité matérielle qui est optimisée pour l’informatique parallèle de données. Un accélérateur peut être un appareil attaché à un bus PCIe (tel qu’un GPU), ou il peut s’agir d’un ensemble d’instructions étendues sur le processeur principal.

## <a name="syntax"></a>Syntaxe

```cpp
class accelerator;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[Constructeur d’accélérateurs](#ctor)|Initialise une nouvelle instance de la classe `accelerator`.|
|[~ Accélérateur (destructeur)](#ctor)|Détruit l’objet `accelerator`.|

### <a name="public-methods"></a>Méthodes publiques

|Nom|Description|
|----------|-----------------|
|[create_view](#create_view)|Crée et retourne un objet `accelerator_view` sur cet accélérateur.|
|[get_all](#get_all)|Retourne un vecteur d’objets `accelerator` qui représentent tous les accélérateurs disponibles.|
|[get_auto_selection_view](#get_auto_selection_view)|Retourne le `accelerator_view`de sélection automatique.|
|[get_dedicated_memory](#get_dedicated_memory)|Retourne la mémoire dédiée pour le `accelerator`, en kilo-octets.|
|[get_default_cpu_access_type](#get_default_cpu_access_type)|Retourne le [access_type](concurrency-namespace-enums-amp.md#access_type) par défaut pour les mémoires tampons créées sur cet accélérateur.|
|[get_default_view](#get_default_view)|Retourne l’objet `accelerator_view` par défaut associé au `accelerator`.|
|[get_description](#get_description)|Retourne une brève description de l’appareil `accelerator`.|
|[get_device_path](#get_device_path)|Retourne le chemin d’accès de l’appareil.|
|[get_has_display](#get_has_display)|Détermine si le `accelerator` est attaché à un affichage.|
|[get_is_debug](#get_is_debug)|Détermine si la couche de débogage de la `accelerator` est activée pour le rapport d’erreurs étendu.|
|[get_is_emulated](#get_is_emulated)|Détermine si la `accelerator` est émulée.|
|[get_supports_cpu_shared_memory](#get_supports_cpu_shared_memory)|Détermine si le `accelerator` prend en charge la mémoire partagée|
|[get_supports_double_precision](#get_supports_double_precision)|Détermine si le `accelerator` est attaché à un affichage.|
|[get_supports_limited_double_precision](#get_supports_limited_double_precision)|Détermine si la `accelerator` a une prise en charge limitée des mathématiques en double précision.|
|[get_version](#get_version)|Retourne la version de la `accelerator`.|
|[set_default](#set_default)|Retourne le chemin d’accès de l’accélérateur par défaut.|
|[set_default_cpu_access_type](#set_default_cpu_access_type)|Définit le [access_type](concurrency-namespace-enums-amp.md#access_type)d’UC par défaut pour les tableaux et les allocations de mémoire implicites effectuées sur ce `accelerator`.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[operator!=](#operator_neq)|Compare cet objet `accelerator` avec un autre et retourne **false** s’ils sont identiques ; Sinon, retourne la **valeur true**.|
|[operator=](#operator_eq)|Copie le contenu de l’objet `accelerator` spécifié dans celui-ci.|
|[operator==](#operator_eq_eq)|Compare cet objet `accelerator` avec un autre et retourne la **valeur true** s’ils sont identiques ; Sinon, retourne **false**.|

### <a name="public-data-members"></a>Membres de données publiques

|Nom|Description|
|----------|-----------------|
|[cpu_accelerator](#cpu_accelerator)|Obtient une constante de chaîne pour le `accelerator`de l’UC.|
|[dedicated_memory](#dedicated_memory)|Obtient la mémoire dédiée pour le `accelerator`, en kilo-octets.|
|[default_accelerator](#default_accelerator)|Obtient une constante de chaîne pour le `accelerator`par défaut.|
|[default_cpu_access_type](#default_cpu_access_type)|Obtient ou définit le [access_type](concurrency-namespace-enums-amp.md#access_type)d’UC par défaut pour les tableaux et les allocations de mémoire implicites effectuées sur ce `accelerator`.|
|[default_view](#default_view)|Obtient l’objet `accelerator_view` par défaut qui est associé à l' `accelerator`.|
|[description](#description)|Obtient une brève description de l’appareil `accelerator`.|
|[device_path](#device_path)|Obtient le chemin d’accès de l’appareil.|
|[direct3d_ref](#direct3d_ref)|Obtient une constante de chaîne pour une `accelerator`de référence Direct3D.|
|[direct3d_warp](#direct3d_warp)|Obtient la constante de chaîne pour un objet `accelerator` que vous pouvez utiliser pour exécuter C++ du code amp sur des processeurs multicœurs qui utilisent des extensions streaming SIMD (SSE).|
|[has_display](#has_display)|Obtient une valeur booléenne qui indique si le `accelerator` est attaché à un affichage.|
|[is_debug](#is_debug)|Indique si la couche de débogage de la `accelerator` est activée pour le rapport d’erreurs étendu.|
|[is_emulated](#is_emulated)|Indique si la `accelerator` est émulée.|
|[supports_cpu_shared_memory](#supports_cpu_shared_memory)|Indique si le `accelerator` prend en charge la mémoire partagée.|
|[supports_double_precision](#supports_double_precision)|Indique si l’accélérateur prend en charge les mathématiques en double précision.|
|[supports_limited_double_precision](#supports_limited_double_precision)|Indique si l’accélérateur prend en charge les mathématiques à double précision de façon limitée.|
|[version](#version)|Obtient la version du `accelerator`.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`accelerator`

## <a name="remarks"></a>Notes

Un accélérateur est une fonctionnalité matérielle qui est optimisée pour l’informatique parallèle de données. Un accélérateur est souvent un GPU discret, mais il peut également s’agir d’une entité côté hôte virtuelle comme un appareil de référence DirectX, d’une distorsion (un appareil côté processeur qui est accéléré par le biais d’instructions SSE) ou du processeur lui-même.

Vous pouvez construire un objet `accelerator` en énumérant les appareils disponibles, ou en obtenant l’appareil par défaut, le périphérique de référence ou le périphérique WARP.

## <a name="requirements"></a>Configuration requise

**En-tête :** amprt. h

**Espace de noms :** Concurrency

## <a name="dtor"></a></a> ~ Accelerator

Détruit l’objet `accelerator`.

```cpp
~accelerator();
```

### <a name="return-value"></a>Valeur de retour

## <a name="ctor"></a>accélérateur

Initialise une nouvelle instance de la [classe d’accélérateur](accelerator-class.md).

```cpp
accelerator();

explicit accelerator(const std::wstring& _Device_path);

accelerator(const accelerator& _Other);
```

### <a name="parameters"></a>Paramètres

*_Device_path*<br/>
Chemin d’accès de l’appareil physique.

*_Other*<br/>
Accélérateur à copier.

## <a name="cpu_accelerator"></a>cpu_accelerator

Obtient une constante de chaîne pour l’accélérateur d’UC.

```cpp
static const wchar_t cpu_accelerator[];
```

## <a name="create_view"></a>create_view

Crée et retourne un objet `accelerator_view` sur cet accélérateur, à l’aide du mode de mise en file d’attente spécifié. Lorsque le mode de mise en file d’attente n’est pas spécifié, le nouveau `accelerator_view` utilise le mode de mise en file d’attente [queuing_mode :: immédiat](concurrency-namespace-enums-amp.md#queuing_mode) .

```cpp
accelerator_view create_view(queuing_mode qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Paramètres

*qmode*<br/>
Mode de mise en file d’attente.

### <a name="return-value"></a>Valeur de retour

Nouvel objet `accelerator_view` sur cet accélérateur, à l’aide du mode de mise en file d’attente spécifié.

## <a name="dedicated_memory"></a>dedicated_memory

Obtient la mémoire dédiée pour le `accelerator`, en kilo-octets.

```cpp
__declspec(property(get= get_dedicated_memory)) size_t dedicated_memory;
```

## <a name="default_accelerator"></a>default_accelerator

Obtient une constante de chaîne pour le `accelerator`par défaut.

```cpp
static const wchar_t default_accelerator[];
```

## <a name="default_cpu_access_type"></a>default_cpu_access_type

[Access_type](concurrency-namespace-enums-amp.md#access_type)d’UC par défaut pour les tableaux et les allocations de mémoire implicites effectuées sur ce `accelerator`.

```cpp
__declspec(property(get= get_default_cpu_access_type)) access_type default_cpu_access_type;
```

## <a name="default_view"></a>default_view

Obtient la vue d’accélérateur par défaut associée au `accelerator`.

```cpp
__declspec(property(get= get_default_view)) accelerator_view default_view;
```

## <a name="description"></a>descriptive

Obtient une brève description de l’appareil `accelerator`.

```cpp
__declspec(property(get= get_description)) std::wstring description;
```

## <a name="device_path"></a>device_path

Obtient le chemin d’accès de l’accélérateur. Le chemin d’accès est unique sur le système.

```cpp
__declspec(property(get= get_device_path)) std::wstring device_path;
```

## <a name="direct3d_ref"></a>direct3d_ref

Obtient une constante de chaîne pour un accélérateur de référence Direct3D.

```cpp
static const wchar_t direct3d_ref[];
```

## <a name="direct3d_warp"></a>direct3d_warp

Obtient la constante de chaîne pour un objet `accelerator` que vous pouvez utiliser pour exécuter votre C++ code amp sur des processeurs multicœurs à l’aide d’extensions streaming SIMD (SSE).

```cpp
static const wchar_t direct3d_warp[];
```

## <a name="get_all"></a>get_all

Retourne un vecteur d’objets `accelerator` qui représentent tous les accélérateurs disponibles.

```cpp
static inline std::vector<accelerator> get_all();
```

### <a name="return-value"></a>Valeur de retour

Vecteur des accélérateurs disponibles

## <a name="get_auto_selection_view"></a>get_auto_selection_view

Retourne le accelerator_view de sélection automatique, qui, lorsqu’il est spécifié en tant que cible de parallel_for_each, permet à la accelerator_view cible d’exécuter le noyau parallel_for_each pour qu’elle soit automatiquement sélectionnée par le Runtime. Dans tous les autres cas, le accelerator_view retourné par cette méthode est le même que le accelerator_view par défaut de l’accélérateur par défaut

```cpp
static accelerator_view __cdecl get_auto_selection_view();
```

### <a name="return-value"></a>Valeur de retour

Accelerator_view de sélection automatique.

## <a name="get_dedicated_memory"></a>get_dedicated_memory

Retourne la mémoire dédiée pour le `accelerator`, en kilo-octets.

```cpp
size_t get_dedicated_memory() const;
```

### <a name="return-value"></a>Valeur de retour

Mémoire dédiée pour le `accelerator`, en kilo-octets.

## <a name="get_default_cpu_access_type"></a>get_default_cpu_access_type

Obtient le access_type d’UC par défaut pour les mémoires tampons créées sur cet accélérateur

```cpp
access_type get_default_cpu_access_type() const;
```

### <a name="return-value"></a>Valeur de retour

Access_type d’UC par défaut pour les mémoires tampons créées sur cet accélérateur.

## <a name="get_default_view"></a>get_default_view

Retourne l’objet `accelerator_view` par défaut associé au `accelerator`.

```cpp
accelerator_view get_default_view() const;
```

### <a name="return-value"></a>Valeur de retour

Objet `accelerator_view` par défaut associé au `accelerator`.

## <a name="get_description"></a>get_description

Retourne une brève description de l’appareil `accelerator`.

```cpp
std::wstring get_description() const;
```

### <a name="return-value"></a>Valeur de retour

Description succincte de l’appareil `accelerator`.

## <a name="get_device_path"></a>get_device_path

Retourne le chemin d’accès de l’accélérateur. Le chemin d’accès est unique sur le système.

```cpp
std::wstring get_device_path() const;
```

### <a name="return-value"></a>Valeur de retour

Chemin d’accès unique à l’instance d’appareil unique au niveau du système.

## <a name="get_has_display"></a>get_has_display

Retourne une valeur booléenne qui indique si la `accelerator` peut sortir d’un affichage.

```cpp
bool get_has_display() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si la `accelerator` peut sortir d’un affichage ; Sinon, **false**.

## <a name="get_is_debug"></a>get_is_debug

Détermine si la couche de débogage de la `accelerator` est activée pour le rapport d’erreurs étendu.

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si la couche de débogage de la `accelerator` est activée pour le rapport d’erreurs étendu. Dans le cas contraire, la valeur est **false**.

## <a name="get_is_emulated"></a>get_is_emulated

Détermine si la `accelerator` est émulée.

```cpp
bool get_is_emulated() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si la `accelerator` est émulée. Dans le cas contraire, la valeur est **false**.

## <a name="get_supports_cpu_shared_memory"></a>get_supports_cpu_shared_memory

Retourne une valeur booléenne indiquant si l’accélérateur prend en charge la mémoire accessible à la fois par l’accélérateur et le processeur.

```cpp
bool get_supports_cpu_shared_memory() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si l’accélérateur prend en charge la mémoire partagée du processeur ; Sinon, **false**.

## <a name="get_supports_double_precision"></a>get_supports_double_precision

Retourne une valeur booléenne qui indique si l’accélérateur prend en charge les opérations mathématiques à double précision, y compris les opérations d’ajout (FMA), de division, de réciproque et de cast de type double, entre **int** et **double**

```cpp
bool get_supports_double_precision() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si l’accélérateur prend en charge les mathématiques à double précision ; Sinon, **false**.

## <a name="get_supports_limited_double_precision"></a>get_supports_limited_double_precision

Retourne une valeur booléenne qui indique si l’accélérateur a une prise en charge limitée pour les opérations mathématiques à double précision. Si l’accélérateur n’a qu’une prise en charge limitée, les possibilités de multiplication de l’ajout (FMA), de division, de réciproque et de conversion fusionnées entre **int** et **double** ne sont pas prises en charge.

```cpp
bool get_supports_limited_double_precision() const;
```

### <a name="return-value"></a>Valeur de retour

**true** si l’accélérateur a une prise en charge limitée des mathématiques à double précision ; Sinon, **false**.

## <a name="get_version"></a>get_version

Retourne la version de la `accelerator`.

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Valeur de retour

Version du `accelerator`.

## <a name="has_display"></a>has_display

Obtient une valeur booléenne qui indique si la `accelerator` peut sortir d’un affichage.

```cpp
__declspec(property(get= get_has_display)) bool has_display;
```

## <a name="is_debug"></a>is_debug

Obtient une valeur booléenne qui indique si la couche de débogage de la `accelerator` est activée pour le rapport d’erreurs étendu.

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="is_emulated"></a>is_emulated

Obtient une valeur booléenne qui indique si la `accelerator` est émulée.

```cpp
__declspec(property(get= get_is_emulated)) bool is_emulated;
```

## <a name="operator_neq"></a>opérateur ! =

Compare cet objet `accelerator` avec un autre et retourne **false** s’ils sont identiques ; Sinon, retourne la **valeur true**.

```cpp
bool operator!= (const accelerator& _Other) const;
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `accelerator` à comparer à celui-ci.

### <a name="return-value"></a>Valeur de retour

**false** si les deux objets `accelerator` sont identiques ; Sinon, **true**.

## <a name="operator_eq"></a>opérateur =

Copie le contenu de l’objet `accelerator` spécifié dans celui-ci.

```cpp
accelerator& operator= (const accelerator& _Other);
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `accelerator` à partir duquel effectuer la copie.

### <a name="return-value"></a>Valeur de retour

Référence à cet objet `accelerator`.

## <a name="operator_eq_eq"></a>opérateur = =

Compare cet objet `accelerator` avec un autre et retourne la **valeur true** s’ils sont identiques ; Sinon, retourne **false**.

```cpp
bool operator== (const accelerator& _Other) const;
```

### <a name="parameters"></a>Paramètres

*_Other*<br/>
Objet `accelerator` à comparer à celui-ci.

### <a name="return-value"></a>Valeur de retour

**true** si l’autre objet `accelerator` est identique à cet objet `accelerator` ; Sinon, **false**.

## <a name="set_default"></a>set_default

Définit l’accélérateur par défaut à utiliser pour toute opération qui utilise implicitement l’accélérateur par défaut. Cette méthode réussit uniquement si l’accélérateur par défaut sélectionné par l’exécution n’a pas déjà été utilisé dans une opération qui utilise implicitement l’accélérateur par défaut

```cpp
static inline bool set_default(std::wstring _Path);
```

### <a name="parameters"></a>Paramètres

*_Path*<br/>
Chemin d’accès à l’accélérateur.

### <a name="return-value"></a>Valeur de retour

**true** si l’appel a lieu lors de la définition de l’accélérateur par défaut. Dans le cas contraire, la valeur est **false**.

## <a name="set_default_cpu_access_type"></a>set_default_cpu_access_type

Définissez le access_type d’UC par défaut pour les tableaux créés sur cet accélérateur ou pour les allocations de mémoire implicites dans le cadre de array_views accessibles sur cet accélérateur. Cette méthode réussit uniquement si le default_cpu_access_type pour l’accélérateur n’a pas déjà été substitué par un appel précédent à cette méthode et que le runtime sélectionné default_cpu_access_type pour cet accélérateur n’a pas encore été utilisé pour allouer un tableau ou pour allocation de mémoire implicite qui stocke une array_view accessible sur cet accélérateur.

```cpp
bool set_default_cpu_access_type(access_type _Default_cpu_access_type);
```

### <a name="parameters"></a>Paramètres

*_Default_cpu_access_type*<br/>
Access_type d’UC par défaut à utiliser pour les allocations de mémoire tableau/array_view sur cet accélérateur.

### <a name="return-value"></a>Valeur de retour

Valeur booléenne indiquant si le access_type d’UC par défaut pour l’accélérateur a été correctement défini.

## <a name="supports_cpu_shared_memory"></a>supports_cpu_shared_memory

Obtient une valeur booléenne indiquant si le `accelerator` prend en charge la mémoire partagée.

```cpp
__declspec(property(get= get_supports_cpu_shared_memory)) bool supports_cpu_shared_memory;
```

## <a name="supports_double_precision"></a>supports_double_precision

Obtient une valeur booléenne qui indique si l’accélérateur prend en charge les mathématiques à double précision.

```cpp
__declspec(property(get= get_supports_double_precision)) bool supports_double_precision;
```

## <a name="supports_limited_double_precision"></a>supports_limited_double_precision

Obtient une valeur booléenne qui indique si l’accélérateur a une prise en charge limitée pour les opérations mathématiques à double précision. Si l’accélérateur n’a qu’une prise en charge limitée, les possibilités de multiplication de l’ajout (FMA), de division, de réciproque et de conversion fusionnées entre `int` et `double` ne sont pas prises en charge.

```cpp
__declspec(property(get= get_supports_limited_double_precision)) bool supports_limited_double_precision;
```

## <a name="version"></a>Version

Obtient la version du `accelerator`.

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="see-also"></a>Voir aussi

[Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
