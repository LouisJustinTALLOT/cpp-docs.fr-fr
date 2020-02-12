---
title: Concurrency::direct3d, fonctions de l’espace de noms (AMP)
ms.date: 08/31/2018
f1_keywords:
- amp/Concurrency::direct3d::abs
- amp/Concurrency::direct3d::countbits
- amp/Concurrency::direct3d::create_accelerator_view
- amp/Concurrency::direct3d::d3d_access_lock
- amp/Concurrency::direct3d::d3d_access_unlock
- amp/Concurrency::direct3d::firstbithigh
- amp/Concurrency::direct3d::get_buffer
- amp/Concurrency::direct3d::get_device
- amp/Concurrency::direct3d::imax
- amp/Concurrency::direct3d::is_timeout_disabled
- amp/Concurrency::direct3d::mad
- amp/Concurrency::direct3d::noise
- amp/Concurrency::direct3d::radians
- amp/Concurrency::direct3d::reversebits
- amp/Concurrency::direct3d::saturate
- amp/Concurrency::direct3d::smoothstep
- amp/Concurrency::direct3d::step
- amp/Concurrency::direct3d::umin
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
ms.openlocfilehash: 438d211ac2f15bf781b704a7d0d7484d1542f131
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127044"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d, fonctions de l’espace de noms (AMP)

||||
|-|-|-|
|[abs](#abs)|[bride](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[IMAX](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[Mad](#mad)|[make_array](#make_array)|[bruit](#noise)|
|[radians](#radians)|[RCP](#rcp)|[reversebits](#reversebits)|
|[saturer](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|
|[première](#step)|[UMAX](#umax)|[umin](#umin)|

## <a name="requirements"></a>Spécifications

**En-tête :** **espace de noms** amp. h : accès concurrentiel

## <a name="abs"></a>  abs

Retourne la valeur absolue de l’argument.

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne la valeur absolue de l’argument.

## <a name="clamp"></a>bride

Calcule la valeur du premier argument spécifié rattaché à une plage définie par les deuxième et troisième arguments spécifiés.

```cpp
inline float clamp(
    float _X,
    float _Min,
    float _Max) restrict(amp);

inline int clamp(
    int _X,
    int _Min,
    int _Max) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à fixer

*_Min*<br/>
Limite inférieure de la plage de verrouillage.

*_Max*<br/>
Limite supérieure de la plage de verrouillage.

### <a name="return-value"></a>Valeur de retour

Valeur de `_X`débloquée.

## <a name="countbits"></a>countbits

Compte le nombre de bits définis dans _X

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière non signée

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de bits définis dans _X

## <a name="create_accelerator_view"></a>create_accelerator_view

Crée un objet [accelerator_view](accelerator-view-class.md) à partir d’un pointeur vers une interface de périphérique Direct3D.

## <a name="syntax"></a>Syntaxe

```cpp
accelerator_view create_accelerator_view(
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```

### <a name="parameters"></a>Paramètres

*_Accelerator*<br/>
Accélérateur sur lequel la nouvelle accelerator_view doit être créée.

*_D3D_device*<br/>
Pointeur vers l’interface de périphérique Direct3D.

*_Disable_timeout*<br/>
Paramètre booléen qui spécifie si le délai d’attente doit être désactivé pour la accelerator_view nouvellement créée. Cela correspond à l’indicateur de D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pour la création de périphérique Direct3D et est utilisé pour indiquer si le système d’exploitation doit autoriser les charges de travail qui prennent plus de 2 secondes à s’exécuter sans réinitialiser l’appareil en fonction du délai d’attente de Windows. mécanisme de détection et de récupération. L’utilisation de cet indicateur est recommandée si vous devez exécuter des tâches de longue durée sur le accelerator_view.

*_Qmode*<br/>
[Queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) à utiliser pour la accelerator_view nouvellement créée. La valeur par défaut de ce paramètre est `queuing_mode_automatic`.

## <a name="return-value"></a>Valeur de retour

Objet `accelerator_view` créé à partir de l’interface d’appareil Direct3D passée.

## <a name="remarks"></a>Notes

Cette fonction crée un objet `accelerator_view` à partir d’un pointeur existant vers une interface de périphérique Direct3D. Si l’appel de fonction a échoué, le décompte de références du paramètre est incrémenté au moyen d’un appel de `AddRef` à l’interface. Vous pouvez libérer en toute sécurité l’objet lorsqu’il n’est plus nécessaire dans votre code DirectX. Si l’appel de la méthode échoue, une [runtime_exception](runtime-exception-class.md) est levée.

L’objet `accelerator_view` que vous créez à l’aide de cette fonction est thread-safe. Vous devez synchroniser l’utilisation simultanée de l’objet `accelerator_view`. L’utilisation simultanée non synchronisée de l’objet `accelerator_view` et de l’interface ID3D11Device brute provoque un comportement indéfini.

Le C++ Runtime amp fournit des informations détaillées sur l’erreur en mode débogage à l’aide de la couche de débogage D3D si vous utilisez l’indicateur `D3D11_CREATE_DEVICE_DEBUG`.

## <a name="d3d_access_lock"></a>d3d_access_lock

Acquérir un verrou sur un accelerator_view dans le but d’effectuer en toute sécurité des opérations D3D sur des ressources partagées avec l’accelerator_view. Le accelerator_view et toutes C++ les ressources amp associées à cet accelerator_view prennent ce verrou en interne lors de l’exécution d’opérations et se bloquent tandis qu’un autre thread détient le verrou d’accès D3D. Ce verrou est non récursif : le comportement n’est pas défini pour appeler cette fonction à partir d’un thread qui détient déjà le verrou. Il s’agit d’un comportement indéfini pour effectuer des opérations sur le accelerator_view ou tout conteneur de données associé au accelerator_view à partir du thread qui détient le verrou d’accès D3D. Voir aussi scoped_d3d_access_lock, une classe de style RAII pour un verrou d’accès D3D basé sur l’étendue.

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Paramètres

*_Av*<br/>
Accelerator_view à verrouiller.

## <a name="d3d_access_try_lock"></a>d3d_access_try_lock

Tentative d’acquisition du verrou d’accès D3D sur un accelerator_view sans blocage.

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Paramètres

*_Av*<br/>
Accelerator_view à verrouiller.

### <a name="return-value"></a>Valeur de retour

true si le verrou a été acquis, ou false s’il est actuellement détenu par un autre thread.

## <a name="d3d_access_unlock"></a>d3d_access_unlock

Libère le verrou d’accès D3D sur le accelerator_view donné. Si le thread appelant ne contient pas le verrou sur le accelerator_view les résultats ne sont pas définis.

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Paramètres

*_Av*<br/>
Accelerator_view pour lequel le verrou doit être libéré.

## <a name="firstbithigh"></a>firstbithigh

Obtient l’emplacement du premier bit défini dans _X, en commençant par le bit d’ordre le plus élevé et en le déplaçant vers le bit d’ordre le plus bas.

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Emplacement du premier bit défini

## <a name="firstbitlow"></a>firstbitlow

Obtient l’emplacement du premier bit défini dans _X, en commençant par le bit d’ordre le plus bas et en travaillant vers le bit d’ordre le plus élevé.

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne l’emplacement du premier bit défini

## <a name="get_buffer"></a>get_buffer

Obtient l’interface de mémoire tampon Direct3D sous-jacente au tableau spécifié.

```cpp
template<
    typename value_type,
    int _Rank
>
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;
```

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Type des éléments dans le tableau.

*_Rank*<br/>
Rang du tableau.

*_Array*<br/>
Tableau sur un accelerator_view Direct3D pour lequel l’interface de mémoire tampon Direct3D sous-jacente est retournée.

### <a name="return-value"></a>Valeur de retour

Pointeur d’interface IUnknown correspondant à la mémoire tampon Direct3D sous-jacente du tableau.

## <a name="a-nameget_device-get_device"></a><a name="get_device"> get_device

Obtenir l’interface d’appareil D3D sous-jacente d’un accelerator_view.

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Paramètres

*Alternatif*<br/>
Accelerator_view D3D pour lequel l’interface d’appareil D3D sous-jacente est retournée.

### <a name="return-value"></a>Valeur retournée

Le pointeur d’interface `IUnknown` de l’appareil D3D sous-jacent du accelerator_view.

## <a name="imax"></a>IMAX

Déterminer la valeur numérique maximale des arguments

```cpp
inline int imax(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

*_Y*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne la valeur numérique maximale des arguments

## <a name="imin"></a>imin

Déterminer la valeur numérique minimale des arguments

```cpp
inline int imin(
    int _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

*_Y*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne la valeur numérique minimale des arguments

## <a name="is_timeout_disabled"></a>is_timeout_disabled

Retourne un indicateur booléen indiquant si le délai d’attente est désactivé pour le accelerator_view spécifié. Cela correspond à l’indicateur de D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pour la création de périphérique Direct3D.

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Paramètres

*_Accelerator_view*<br/>
Accelerator_view pour lequel le paramètre timeout Disabled doit être interrogé.

### <a name="return-value"></a>Valeur de retour

Indicateur booléen indiquant si le délai d’attente est désactivé pour le accelerator_view spécifié.

## <a name="mad"></a>Mad

Calcule le produit du premier et du deuxième argument spécifié, puis ajoute le troisième argument spécifié.

```cpp
inline float mad(
    float _X,
    float _Y,
    float _Z) restrict(amp);

inline double mad(
    double _X,
    double _Y,
    double _Z) restrict(amp);

inline int mad(
    int _X,
    int _Y,
    int _Z) restrict(amp);

inline unsigned int mad(
    unsigned int _X,
    unsigned int _Y,
    unsigned int _Z) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Premier argument spécifié.

*_Y*<br/>
Deuxième argument spécifié.

*_Z*<br/>
Troisième argument spécifié.

### <a name="return-value"></a>Valeur de retour

Résultat de `_X` \* `_Y` + `_Z`.

## <a name="make_array"></a>make_array

Créez un tableau à partir d’un pointeur d’interface de mémoire tampon Direct3D.

```cpp
template<
    typename value_type,
    int _Rank
>
array<value_type, _Rank> make_array(
    const extent<_Rank>& _Extent,
    const Concurrency::accelerator_view& _Rv,
    IUnknown* _D3D_buffer)  ;
```

### <a name="parameters"></a>Paramètres

*value_type*<br/>
Type d’élément du tableau à créer.

*_Rank*<br/>
Rang du tableau à créer.

*_Extent*<br/>
Une extension qui décrit la forme de l’agrégat de tableau.

*_Rv*<br/>
Vue d’accélérateur D3D sur laquelle le tableau doit être créé.

*_D3D_buffer*<br/>
Pointeur d’interface IUnknown de la mémoire tampon D3D à partir duquel créer le tableau.

### <a name="return-value"></a>Valeur de retour

Tableau créé à l’aide de la mémoire tampon Direct3D fournie.

## <a name="noise"></a>bruit

Génère une valeur aléatoire à l’aide de l’algorithme de bruit perl

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante à partir de laquelle générer un bruit perl

### <a name="return-value"></a>Valeur de retour

Retourne la valeur de bruit perl dans une plage comprise entre-1 et 1

## <a name="radians"></a>radians

Convertit _X de degrés en radians

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne _X convertis de degrés en radians

## <a name="rcp"></a>RCP

Calcule la réciproque de l’argument spécifié à l’aide d’une approximation rapide.

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur pour laquelle calculer la réciproque.

### <a name="return-value"></a>Valeur de retour

Réciproque de l’argument spécifié.

## <a name="reversebits"></a>reversebits

Inverse l’ordre des bits dans _X

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière non signée

### <a name="return-value"></a>Valeur de retour

Retourne la valeur avec l’ordre de bits inversé dans _X

## <a name="saturate"></a>saturer

Attache _X dans la plage comprise entre 0 et 1

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne _X ancré dans la plage comprise entre 0 et 1

## <a name="sign"></a>expéditeur

Détermine le signe de l’argument spécifié.

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Signe de l’argument.

## <a name="smoothstep"></a>smoothstep

Retourne une interpolation Smooth Hermite entre 0 et 1, si _X se trouve dans la plage [_Min, _Max].

```cpp
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Min*<br/>
Valeur à virgule flottante

*_Max*<br/>
Valeur à virgule flottante

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne 0 si _X est inférieur à _Min ; 1 si la _X est supérieure à _Max ; Sinon, une valeur comprise entre 0 et 1 si _X se trouve dans la plage [_Min, _Max]

## <a name="step"></a>première

Compare deux valeurs, en retournant 0 ou 1 en fonction de la valeur la plus élevée

```cpp
inline float step(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_Y*<br/>
Valeur à virgule flottante

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retourne 1 si la _X est supérieure ou égale à _Y ; dans le cas contraire, 0

## <a name="umax"></a>UMAX

Déterminer la valeur numérique maximale des arguments

```cpp
inline unsigned int umax(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

*_Y*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne la valeur numérique maximale des arguments

## <a name="umin"></a>umin

Déterminer la valeur numérique minimale des arguments

```cpp
inline unsigned int umin(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

*_Y*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne la valeur numérique minimale des arguments

## <a name="see-also"></a>Voir aussi

[Concurrency::direct3d, espace de noms](concurrency-direct3d-namespace.md)
