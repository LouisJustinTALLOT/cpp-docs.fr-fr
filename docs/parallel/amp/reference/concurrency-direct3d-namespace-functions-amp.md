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
ms.openlocfilehash: e21b1f2869ab81973b341abc5371714fbf8580e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375936"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Concurrency::direct3d, fonctions de l’espace de noms (AMP)

||||
|-|-|-|
|[Abs](#abs)|[Pince](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[Imax](#imax)|[Imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[Fou](#mad)|[make_array](#make_array)|[Bruit](#noise)|
|[Radians](#radians)|[rcp](#rcp)|[revers](#reversebits)|
|[Saturer](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|
|[Étape](#step)|[Umax](#umax)|[umin umin](#umin)|

## <a name="requirements"></a>Spécifications

**En-tête:** amp.h **Namespace:** Concurrency

## <a name="abs"></a><a name="abs"></a>Abs

Retourne la valeur absolue de l’argument

```cpp
inline int abs(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retourne la valeur absolue de l’argument.

## <a name="clamp"></a><a name="clamp"></a>Pince

Calcule la valeur du premier argument spécifié serré à une fourchette définie par les deuxième et troisième arguments spécifiés.

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
La valeur à serrer

*_Min*<br/>
La limite inférieure de la plage de serrage.

*_Max*<br/>
La limite supérieure de la plage de serrage.

### <a name="return-value"></a>Valeur de retour

La valeur serrée `_X`de .

## <a name="countbits"></a><a name="countbits"></a>countbits

Compte le nombre de bits de set dans _X

```cpp
inline unsigned int countbits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur insignable

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de bits de set dans _X

## <a name="create_accelerator_view"></a><a name="create_accelerator_view"></a>create_accelerator_view

Crée un [objet accelerator_view](accelerator-view-class.md) d’un pointeur à une interface d’appareil Direct3D.

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
L’accélérateur sur lequel le nouveau accelerator_view doit être créé.

*_D3D_device*<br/>
Le pointeur de l’interface de l’appareil Direct3D.

*_Disable_timeout*<br/>
Un paramètre Boolean qui précise si le délai d’attente doit être désactivé pour le accelerator_view nouvellement créé. Cela correspond au D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT drapeau pour la création de l’appareil Direct3D et est utilisé pour indiquer si le système d’exploitation devrait permettre aux charges de travail qui prennent plus de 2 secondes à exécuter sans réinitialiser l’appareil par le mécanisme de détection et de récupération des délais Windows. L’utilisation de ce drapeau est recommandée si vous avez besoin d’effectuer des tâches longues sur le accelerator_view.

*_Qmode*<br/>
Le [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) à utiliser pour le accelerator_view nouvellement créé. Ce paramètre a `queuing_mode_automatic`une valeur par défaut de .

## <a name="return-value"></a>Valeur de retour

L’objet `accelerator_view` créé à partir de l’interface de périphérique Direct3D passée.

## <a name="remarks"></a>Notes

Cette fonction crée `accelerator_view` un nouvel objet d’un pointeur existant à une interface appareil Direct3D. Si l’appel de fonction réussit, le nombre de références `AddRef` du paramètre est incrémenté au moyen d’un appel à l’interface. Vous pouvez libérer l’objet en toute sécurité lorsqu’il n’est plus requis dans votre code DirectX. Si l’appel de méthode échoue, un [runtime_exception](runtime-exception-class.md) est lancé.

L’objet `accelerator_view` que vous créez en utilisant cette fonction est sans danger pour le thread. Vous devez synchroniser l’utilisation simultanée de l’objet. `accelerator_view` L’utilisation simultanée non synchronisée de l’objet `accelerator_view` et de l’interface raw ID3D11Device provoque un comportement indéfini.

Le temps d’exécution DE l’AMP CMD fournit des informations détaillées sur les erreurs `D3D11_CREATE_DEVICE_DEBUG` en mode débogé en utilisant la couche D3D Debug si vous utilisez le drapeau.

## <a name="d3d_access_lock"></a><a name="d3d_access_lock"></a>d3d_access_lock

Acquérir un verrou sur un accelerator_view dans le but d’effectuer en toute sécurité les opérations D3D sur les ressources partagées avec le accelerator_view. Le accelerator_view et toutes les ressources AMP de CMD associées à cette accelerator_view à l’interne prennent ce verrou lors de l’exécution des opérations et bloqueront tandis qu’un autre thread tient le verrou d’accès D3D. Ce verrou n’est pas récursif: Il est un comportement indéfini d’appeler cette fonction à partir d’un thread qui détient déjà le verrou. Il est un comportement indéfini d’effectuer des opérations sur le accelerator_view ou tout conteneur de données associé à la accelerator_view à partir du thread qui détient le verrou d’accès D3D. Voir aussi scoped_d3d_access_lock, une classe de style RAII pour un verrou d’accès D3D basé sur la portée.

```cpp
void __cdecl d3d_access_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Paramètres

*_Av*<br/>
Le accelerator_view à verrouiller.

## <a name="d3d_access_try_lock"></a><a name="d3d_access_try_lock"></a>d3d_access_try_lock

Tentative d’acquisition du verrou d’accès D3D sur une accelerator_view sans blocage.

```cpp
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```

### <a name="parameters"></a>Paramètres

*_Av*<br/>
Le accelerator_view à verrouiller.

### <a name="return-value"></a>Valeur de retour

vrai si le verrou a été acquis, ou faux si elle est actuellement détenue par un autre thread.

## <a name="d3d_access_unlock"></a><a name="d3d_access_unlock"></a>d3d_access_unlock

Relâchez le verrou d’accès D3D sur le accelerator_view donné. Si le fil d’appel ne tient pas le verrou sur le accelerator_view les résultats ne sont pas définis.

```cpp
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```

### <a name="parameters"></a>Paramètres

*_Av*<br/>
Le accelerator_view pour lequel la serrure doit être libérée.

## <a name="firstbithigh"></a><a name="firstbithigh"></a>firstbithigh

Obtient l’emplacement du premier bit ensemble dans _X, en commençant par le bit de haut ordre et se déplaçant vers le bit le plus bas-ordre.

```cpp
inline int firstbithigh(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

L’emplacement du premier set bit

## <a name="firstbitlow"></a><a name="firstbitlow"></a>firstbitlow

Obtient l’emplacement du premier bit ensemble dans _X, en commençant par le bit le plus bas-ordre et de travailler vers le bit de haut ordre.

```cpp
inline int firstbitlow(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Retours L’emplacement du premier set

## <a name="get_buffer"></a><a name="get_buffer"></a>get_buffer

Obtenez l’interface tampon Direct3D sous-jacente au tableau spécifié.

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
Un tableau sur un accelerator_view Direct3D pour lequel l’interface tampon directe sous-jacente est retournée.

### <a name="return-value"></a>Valeur de retour

Le pointeur d’interface IUnknown correspondant au tampon Direct3D sous-jacent au tableau.

## <a name="a-nameget_device-get_device"></a><a name="get_device">get_device

Obtenez l’interface de périphérique D3D sous-jacente à un accelerator_view.

```cpp
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Paramètres

*Av*<br/>
Le accelerator_view D3D pour lequel l’interface sous-jacente de l’appareil D3D est retournée.

### <a name="return-value"></a>Valeur retournée

Le `IUnknown` pointeur d’interface de l’appareil D3D sous-jacent à la accelerator_view.

## <a name="imax"></a><a name="imax"></a>Imax

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

Retourner la valeur numérique maximale des arguments

## <a name="imin"></a><a name="imin"></a>Imin

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

Retourner la valeur numérique minimale des arguments

## <a name="is_timeout_disabled"></a><a name="is_timeout_disabled"></a>is_timeout_disabled

Retourne un drapeau boolean indiquant si le délai d’attente est désactivé pour les accelerator_view spécifiés. Cela correspond au drapeau D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pour la création d’appareils Direct3D.

```cpp
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```

### <a name="parameters"></a>Paramètres

*_Accelerator_view*<br/>
La accelerator_view pour laquelle le délai d’attente désactivé réglage doit être interrogé.

### <a name="return-value"></a>Valeur de retour

Un drapeau boolean indiquant si le délai d’attente est désactivé pour les accelerator_view spécifiés.

## <a name="mad"></a><a name="mad"></a>Fou

Calcule le produit de la première et la deuxième argument spécifiée, puis ajoute le troisième argument spécifié.

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
Le premier argument spécifié.

*_Y*<br/>
Le deuxième argument spécifié.

*_Z*<br/>
Le troisième argument spécifié.

### <a name="return-value"></a>Valeur de retour

Le résultat `_X` \* `_Y`  +  `_Z`de .

## <a name="make_array"></a><a name="make_array"></a>make_array

Créez un tableau à partir d’un pointeur d’interface tampon Direct3D.

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
Le type d’élément du tableau à créer.

*_Rank*<br/>
Le rang du tableau à créer.

*_Extent*<br/>
Une mesure qui décrit la forme de l’agrégat de tableau.

*_Rv*<br/>
Une vue d’accélérateur D3D sur laquelle le tableau doit être créé.

*_D3D_buffer*<br/>
IUnknown interface pointeur de la mémoire tampon D3D pour créer le tableau à partir.

### <a name="return-value"></a>Valeur de retour

Un tableau créé à l’aide du tampon Direct3D fourni.

## <a name="noise"></a><a name="noise"></a>Bruit

Génère une valeur aléatoire à l’aide de l’algorithme de bruit Perlin

```cpp
inline float noise(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur de point flottant à partir de laquelle générer le bruit de Perlin

### <a name="return-value"></a>Valeur de retour

Retourne La valeur sonore Perlin dans une fourchette comprise entre -1 et 1

## <a name="radians"></a><a name="radians"></a>Radians

Convertit _X de degrés en radians

```cpp
inline float radians(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retours _X convertis de degrés en radians

## <a name="rcp"></a><a name="rcp"></a>Rcp

Calcule la réciprocité de l’argument spécifié en utilisant une approximation rapide.

```cpp
inline float rcp(float _X) restrict(amp);

inline double rcp(double _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
La valeur pour laquelle calculer la réciprocité.

### <a name="return-value"></a>Valeur de retour

La réciprocité de l’argument spécifié.

## <a name="reversebits"></a><a name="reversebits"></a>revers

Inverse l’ordre des bits dans _X

```cpp
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur insignable

### <a name="return-value"></a>Valeur de retour

Retourne la valeur avec l’ordre de bit inversé dans _X

## <a name="saturate"></a><a name="saturate"></a>Saturer

Les pinces _X dans la fourchette de 0 à 1

```cpp
inline float saturate(float _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour

Retours _X serrés dans la fourchette de 0 à 1

## <a name="sign"></a><a name="sign"></a>Signe

Détermine le signe de l’argument spécifié.

```cpp
inline int sign(int _X) restrict(amp);
```

### <a name="parameters"></a>Paramètres

*_X*<br/>
Valeur entière

### <a name="return-value"></a>Valeur de retour

Le signe de l’argument.

## <a name="smoothstep"></a><a name="smoothstep"></a>smoothstep

Retourne une interpolation Hermite lisse entre 0 et 1, si _X est dans la gamme [_Min, _Max].

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

Retours 0 si _X est inférieur à _Min; 1 si _X est plus grande que _Max; autrement, une valeur comprise entre 0 et 1 si _X est dans la fourchette [_Min, _Max]

## <a name="step"></a><a name="step"></a>Étape

Compare deux valeurs, le retour de 0 ou 1 en fonction de la valeur

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

Retourne 1 si le _X est supérieur ou égal à _Y; autrement, 0

## <a name="umax"></a><a name="umax"></a>Umax

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

Retourner la valeur numérique maximale des arguments

## <a name="umin"></a><a name="umin"></a>umin umin

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

Retourner la valeur numérique minimale des arguments

## <a name="see-also"></a>Voir aussi

[Concurrency::direct3d, espace de noms](concurrency-direct3d-namespace.md)
