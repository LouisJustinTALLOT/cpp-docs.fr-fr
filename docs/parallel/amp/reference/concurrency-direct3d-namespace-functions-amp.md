---
title: Les fonctions d’espace de noms (AMP) Concurrency::Direct3D | Microsoft Docs
ms.custom: ''
ms.date: 08/31/2018
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 28943b62-52c9-42dc-baf1-ca7b095c1a19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 099bd36908ef12d2cd4c6b4603dc047d7ed6e74f
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107601"
---
# <a name="concurrencydirect3d-namespace-functions-amp"></a>Fonctions Concurrency::Direct3D de l’espace de noms (AMP)
||||
|-|-|-|
|[abs](#abs)|[clamp](#clamp)|[countbits](#countbits)|
|[create_accelerator_view](#create_accelerator_view)|[d3d_access_lock](#d3d_access_lock)||
|[d3d_access_try_lock](#d3d_access_try_lock)|[d3d_access_unlock](#d3d_access_unlock)|[firstbithigh](#firstbithigh)|
|[firstbitlow](#firstbitlow)|[get_buffer](#get_buffer)|[get_device](#get_device)|
|[imax](#imax)|[imin](#imin)|[is_timeout_disabled](#is_timeout_disabled)|
|[mad](#mad)|[make_array](#make_array)|[bruit](#noise)|
|[radians](#radians)|[rcp](#rcp)|[reversebits](#reversebits)|
|[saturate](#saturate)|[sign](#sign)|[smoothstep](#smoothstep)|
|[step](#step)|[umax](#umax)|[umin](#umin)|

## <a name="requirements"></a>Configuration requise
**En-tête :** amp.h **Namespace :** accès concurrentiel

##  <a name="abs"></a>  abs
Retourne la valeur absolue de l’argument

```  
inline int abs(int _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur entière

### <a name="return-value"></a>Valeur de retour
Retourne la valeur absolue de l’argument.

##  <a name="clamp"></a>  Clamp
Calcule la valeur du premier argument spécifié ancré dans une plage définie par les deuxième et troisième arguments spécifiés.

```  
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
`_X`  
La valeur à ancrer.

`_Min`  
La limite inférieure de la plage d’ancrage.

`_Max`  
La limite supérieure de la plage d’ancrage.

### <a name="return-value"></a>Valeur de retour
Valeur ancrée de `_X`.

##  <a name="countbits"></a>  countbits
Compte le nombre de bits dans _X

```  
inline unsigned int countbits(unsigned int _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur entière non signée

### <a name="return-value"></a>Valeur de retour
Retourne le nombre de bits dans _X

## <a name="create_accelerator_view"></a> create_accelerator_view
Crée un [accelerator_view](accelerator-view-class.md) objet à partir d’un pointeur vers une interface de périphérique Direct3D.

## <a name="syntax"></a>Syntaxe

```  
accelerator_view create_accelerator_view(  
    IUnknown * _D3D_device
    queuing_mode _Qmode = queuing_mode_automatic);

accelerator_view create_accelerator_view(  
    accelerator& _Accelerator,
    bool _Disable_timeout
    queuing_mode _Qmode = queuing_mode_automatic);
```  

#### <a name="parameters"></a>Paramètres
`_Accelerator`  
L’accélérateur sur lequel le nouveau new_accelerator doit être créé.

`_D3D_device`  
Pointeur vers l’interface de périphérique Direct3D.

`_Disable_timeout`  
Un paramètre booléen qui spécifie si le délai d’expiration doit être désactivée pour l’accelerator_view qui vient d’être créée. Cela correspond à l’indicateur D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pour la création de périphérique Direct3D et est utilisé pour indiquer si le système d’exploitation doit autoriser les charges de travail qui prennent plus de 2 secondes à s’exécuter sans réinitialiser l’appareil par le délai d’attente de Windows mécanisme de détection et de récupération. Utilisation de cet indicateur est recommandée si vous avez besoin effectuer des tâches de longue durée sur accelerator_view.

`_Qmode`  
Le [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) à utiliser pour l’accelerator_view qui vient d’être créée. Ce paramètre a la valeur par défaut `queuing_mode_automatic`.

## <a name="return-value"></a>Valeur de retour
Le `accelerator_view` objet créé à partir de l’interface de périphérique Direct3D passée.

## <a name="remarks"></a>Notes
Cette fonction crée un nouveau `accelerator_view` objet à partir d’un pointeur existant vers une interface de périphérique Direct3D. Si l’appel de fonction réussit, le décompte de références du paramètre est incrémenté d’un `AddRef` appel à l’interface. Vous pouvez libérer en toute sécurité de l’objet lorsqu’il n’est plus nécessaire dans votre code DirectX. Si l’appel de méthode échoue, un [runtime_exception](runtime-exception-class.md) est levée.

Le `accelerator_view` objet que vous créez à l’aide de cette fonction est thread-safe. Vous devez synchroniser utilisation simultanée de la `accelerator_view` objet. Utilisation simultanée de non le `accelerator_view` objet et l’interface ID3D11Device brute provoque un comportement indéfini.

Le runtime C++ AMP fournit des informations d’erreur détaillées en mode débogage à l’aide de la couche de débogage D3D si vous utilisez le `D3D11_CREATE_DEVICE_DEBUG` indicateur.


##  <a name="d3d_access_lock"></a>  d3d_access_lock
Acquérir un verrou sur un accelerator_view pour exécuter sans risque les opérations D3D sur les ressources partagées avec l’accelerator_view. L’accelerator_view et toutes les ressources de C++ AMP associés à cet accelerator_view en interne prennent ce verrou lors des opérations et se bloquent lorsqu’un autre thread détient le verrou d’accès D3D. Ce verrou est non-récursif : il correspond à un comportement d’appeler cette fonction à partir d’un thread qui détient déjà le verrou. Il est un comportement non défini pour effectuer des opérations sur l’accelerator_view ou de n’importe quel conteneur de données associées à accelerator_view du thread qui détient le verrou d’accès D3D. Voir également scoped_d3d_access_lock, une classe de style RAII pour un verrou d’accès D3D basée sur l’étendue.

```  
void __cdecl d3d_access_lock(accelerator_view& _Av);
```  

### <a name="parameters"></a>Paramètres
`_Av`  
Accelerator_view à verrouiller.

##  <a name="d3d_access_try_lock"></a>  d3d_access_try_lock
Tenter d’acquérir le verrou d’accès D3D sur un accelerator_view sans blocage.

```  
bool __cdecl d3d_access_try_lock(accelerator_view& _Av);
```  

### <a name="parameters"></a>Paramètres
`_Av`  
Accelerator_view à verrouiller.

### <a name="return-value"></a>Valeur de retour
True si le verrou a été acquis, ou false si elle est actuellement détenu par un autre thread.

##  <a name="d3d_access_unlock"></a>  d3d_access_unlock
Libérer le verrou d’accès D3D sur l’accelerator_view donné. Si le thread appelant ne contient pas le verrou sur accelerator_view, les résultats sont indéfinis.

```  
void __cdecl d3d_access_unlock(accelerator_view& _Av);
```  

### <a name="parameters"></a>Paramètres
`_Av`  
L’accelerator_view pour lequel le verrou doit être libéré.

##  <a name="firstbithigh"></a>  firstbithigh
Obtient l’emplacement du premier bit défini dans _X, en commençant par le bit d’ordre le plus élevé et la migration vers le bit le plus bas.

```  
inline int firstbithigh(int _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur entière

### <a name="return-value"></a>Valeur de retour
L’emplacement du premier bit défini

##  <a name="firstbitlow"></a>  firstbitlow
Obtient l’emplacement du premier bit défini dans _X, en commençant avec le bit le plus bas et vers le bit d’ordre le plus élevé.

```  
inline int firstbitlow(int _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur entière

### <a name="return-value"></a>Valeur de retour
Retourne l’emplacement du premier bit défini

##  <a name="get_buffer"></a>  get_buffer
Obtenir l’interface de mémoire tampon Direct3D sous-jacente au tableau spécifié.

```  
template<
    typename value_type,
    int _Rank
>
IUnknown *get_buffer(
    const array<value_type, _Rank>& _Array)  ;
```  

### <a name="parameters"></a>Paramètres
`value_type`  
Type des éléments dans le tableau.

`_Rank`  
Le rang du tableau.

`_Array`  
Un tableau sur un accelerator_view Direct3D pour lequel l’interface de mémoire tampon Direct3D sous-jacente est retournée.

### <a name="return-value"></a>Valeur de retour
Le pointeur d’interface IUnknown correspondant à la mémoire tampon de Direct3D sous-jacente du tableau.

## <a name="a-namegetdevice-getdevice"></a><a name="get_device"> get_device
Obtenir l’interface de périphérique D3D sous-jacente d’un accelerator_view.

```
IUnknown* get_device(const accelerator_view Av);
```

### <a name="parameters"></a>Paramètres
*Violation d’accès*<br/>
L’accelerator_view D3D pour lequel l’interface de périphérique D3D sous-jacente est retournée.


### <a name="return-value"></a>Valeur de retour
Le `IUnknown` pointeur d’interface du périphérique D3D sous-jacente de l’accelerator_view.

##  <a name="imax"></a>  imax
Déterminer la valeur numérique maximale des arguments

```  
inline int imax(
    int _X,
    int _Y) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur entière

`_Y`  
Valeur entière

### <a name="return-value"></a>Valeur de retour
Retourne la valeur numérique maximale des arguments

##  <a name="imin"></a>  imin
Déterminer la valeur numérique minimale des arguments

```  
inline int imin(
    int _X,
    int _Y) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur entière

`_Y`  
Valeur entière

### <a name="return-value"></a>Valeur de retour
Retourne la valeur numérique minimale des arguments

##  <a name="is_timeout_disabled"></a>  is_timeout_disabled
Retourne un indicateur booléen indiquant si le délai d’attente est désactivé pour l’accelerator_view spécifié. Cela correspond à l’indicateur D3D11_CREATE_DEVICE_DISABLE_GPU_TIMEOUT pour la création de périphérique Direct3D.

```  
bool __cdecl is_timeout_disabled(const accelerator_view& _Accelerator_view);
```  

### <a name="parameters"></a>Paramètres
`_Accelerator_view`  
L’accelerator_view pour lequel le paramètre de délai désactivé doit être interrogé.

### <a name="return-value"></a>Valeur de retour
Un indicateur booléen indiquant si le délai d’attente est désactivé pour l’accelerator_view spécifié.

##  <a name="mad"></a>  mad
Calcule le produit de la première et deuxième argument spécifié, puis ajoute le troisième argument spécifié.

```  
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
`_X`  
Le premier argument spécifié.

`_Y`  
Le deuxième argument spécifié.

`_Z`  
Le troisième argument spécifié.

### <a name="return-value"></a>Valeur de retour
Le résultat de `_X` \* `_Y`  +  `_Z`.

##  <a name="make_array"></a>  make_array
Créer un tableau à partir d’un pointeur d’interface de mémoire tampon Direct3D.

```  
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
`value_type`  
Le type d’élément du tableau à créer.

`_Rank`  
Le rang du tableau à créer.

`_Extent`  
Une étendue qui décrit la forme de l’agrégat de tableau.

`_Rv`  
Une vue d’accélérateur D3D sur laquelle le tableau doit être créé.

`_D3D_buffer`  
Pointeur d’interface IUnknown de la mémoire tampon D3D pour créer le tableau à partir de.

### <a name="return-value"></a>Valeur de retour
Tableau créé à l’aide de la mémoire tampon Direct3D fournie.

##  <a name="noise"></a>  noise
Génère une valeur aléatoire à l’aide de l’algorithme de bruit de Perlin

```  
inline float noise(float _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur à virgule flottante à partir duquel générer le bruit de Perlin

### <a name="return-value"></a>Valeur de retour
Retourne la valeur de bruit de Perlin The dans une plage comprise entre -1 et 1

##  <a name="radians"></a>  radians
Convertit _X de degrés en radians.

```  
inline float radians(float _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour
Retourne _X converti à partir de degrés en radians.

##  <a name="rcp"></a>  rcp
Calcule le réciproque de l’argument spécifié à l’aide d’une approximation rapide.

```  
inline float rcp(float _X) restrict(amp);


inline double rcp(double _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
La valeur pour laquelle la réciproque.

### <a name="return-value"></a>Valeur de retour
Réciproque de l’argument spécifié.

##  <a name="reversebits"></a>  reversebits
Inverse l’ordre des bits dans _X

```  
inline unsigned int reversebits(unsigned int _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur entière non signée

### <a name="return-value"></a>Valeur de retour
Retourne la valeur avec l’ordre des bits inversé dans _X

##  <a name="saturate"></a>  saturer
Fixe _X dans la plage de 0 à 1

```  
inline float saturate(float _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour
Retourne _X ancrée dans la plage de 0 à 1

##  <a name="sign"></a>  sign
Détermine le signe de l’argument spécifié.

```  
inline int sign(int _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur entière

### <a name="return-value"></a>Valeur de retour
Le signe de l’argument.

##  <a name="smoothstep"></a>  smoothstep
Retourne une interpolation Hermite fluide entre 0 et 1, si _X se trouve dans la plage [_Min, _Max].

```  
inline float smoothstep(
    float _Min,
    float _Max,
    float _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_Min`  
Valeur à virgule flottante

`_Max`  
Valeur à virgule flottante

`_X`  
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour
Retourne 0 si _X est inférieure à _Min ; 1 si _X est supérieure à _Max ; Sinon, une valeur comprise entre 0 et 1 si _X se trouve dans la plage [_Min, _Max]

##  <a name="step"></a>  Étape
Compare deux valeurs, retourne 0 ou 1 selon la valeur est supérieure

```  
inline float step(
    float _Y,
    float _X) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_Y`  
Valeur à virgule flottante

`_X`  
Valeur à virgule flottante

### <a name="return-value"></a>Valeur de retour
Retourne 1 si le _X est supérieur ou égal à _Y ; Sinon, 0

##  <a name="umax"></a>  umax
Déterminer la valeur numérique maximale des arguments

```  
inline unsigned int umax(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur entière

`_Y`  
Valeur entière

### <a name="return-value"></a>Valeur de retour
Retourne la valeur numérique maximale des arguments

##  <a name="umin"></a>  umin
Déterminer la valeur numérique minimale des arguments

```  
inline unsigned int umin(
    unsigned int _X,
    unsigned int _Y) restrict(amp);
```  

### <a name="parameters"></a>Paramètres
`_X`  
Valeur entière

`_Y`  
Valeur entière

### <a name="return-value"></a>Valeur de retour
Retourne la valeur numérique minimale des arguments

## <a name="see-also"></a>Voir aussi
[Concurrency::direct3d, espace de noms](concurrency-direct3d-namespace.md)
