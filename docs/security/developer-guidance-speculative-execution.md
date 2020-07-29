---
title: Guide de développement C++ pour les canaux côté exécution spéculative
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: d0b9faf0bd11892c05e25e981e8cd729cb623dd4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219324"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>Guide de développement C++ pour les canaux côté exécution spéculative

Cet article contient des conseils pour les développeurs qui aident à identifier et à atténuer les vulnérabilités matérielles du canal côté exécution spéculative dans le logiciel C++. Ces vulnérabilités peuvent divulguer des informations sensibles à travers les limites d’approbation et peuvent affecter des logiciels qui s’exécutent sur des processeurs qui prennent en charge l’exécution spéculative et non ordonnée des instructions. Cette classe de vulnérabilités a été décrite en janvier 2018 et des informations et des informations supplémentaires sont disponibles dans l' [avis de sécurité de Microsoft](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002).

L’aide fournie dans cet article est liée aux classes de vulnérabilités représentées par :

1. CVE-2017-5753, également appelé spectre variant 1. Cette classe de vulnérabilité matérielle est liée aux canaux secondaires qui peuvent survenir en raison d’une exécution spéculative qui se produit à la suite d’une prédiction incorrecte de branche conditionnelle. Le compilateur Microsoft C++ dans Visual Studio 2017 (à partir de la version 15.5.5) inclut la prise en charge du `/Qspectre` commutateur qui fournit une atténuation au moment de la compilation pour un ensemble limité de modèles de codage potentiellement vulnérables associés à CVE-2017-5753. Le `/Qspectre` commutateur est également disponible dans Visual Studio 2015 Update 3 à [KB 4338871](https://support.microsoft.com/help/4338871). La documentation de l’indicateur [/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre) fournit plus d’informations sur ses effets et son utilisation.

2. CVE-2018-3639, également appelé « [contournement de la Banque spéculative » (SSB)](https://aka.ms/sescsrdssb). Cette classe de vulnérabilité matérielle est liée aux canaux secondaires qui peuvent survenir en raison de l’exécution spéculative d’une charge à l’avance d’un magasin dépendant suite à une prédiction d’accès à la mémoire.

Une présentation accessible aux vulnérabilités de canal côté exécution spéculative est disponible dans la présentation intitulée [spectre et Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) de l’une des équipes de recherche ayant découvert ces problèmes.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>Quelles sont les vulnérabilités matérielles des canaux côté exécution spéculative ?

Les processeurs modernes offrent des niveaux de performances plus élevés en utilisant des instructions spéculatives et non ordonnées. C’est le cas, par exemple, en prédisant la cible des branches (conditionnelles et indirectes), ce qui permet au processeur de commencer à exécuter de manière spéculative des instructions au niveau de la cible de la branche prédite, évitant ainsi un blocage jusqu’à ce que la cible réelle de la branche soit résolue. Dans le cas où l’UC Découvre plus tard qu’une prédiction s’est produite, tout l’état de l’ordinateur qui a été calculé de manière spéculative est ignoré. Cela garantit qu’il n’existe aucun effet visuellement visible de la spéculation non prédite.

Alors que l’exécution spéculative n’affecte pas l’état visible de l’architecture, elle peut conserver les traces résiduelles dans un État non architectural, comme les différents caches utilisés par le processeur. Il s’agit de traces résiduelles d’exécution spéculative qui peuvent donner lieu à des vulnérabilités de canal latérale. Pour mieux comprendre cela, examinez le fragment de code suivant qui fournit un exemple de CVE-2017-5753 (contournement du contrôle des limites) :

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

Dans cet exemple, `ReadByte` est fourni une mémoire tampon, une taille de mémoire tampon et un index dans cette mémoire tampon. Le paramètre d’index, tel que spécifié par `untrusted_index` , est fourni par un contexte moins privilégié, tel qu’un processus non administratif. Si `untrusted_index` est inférieur à `buffer_size` , le caractère au niveau de cet index est lu `buffer` et utilisé pour l’indexer dans une région partagée de mémoire référencée par `shared_buffer` .

D’un point de vue architectural, cette séquence de code est parfaitement sécurisée, car elle est `untrusted_index` toujours inférieure à `buffer_size` . Toutefois, en cas d’exécution spéculative, il est possible que l’UC prédictionte la branche conditionnelle et exécute le corps de l’instruction if même si `untrusted_index` est supérieur ou égal à `buffer_size` . Par conséquent, le processeur peut lire de manière spéculative un octet au-delà des limites de `buffer` (qui peut être un secret) et peut ensuite utiliser cette valeur d’octet pour calculer l’adresse d’une charge ultérieure via `shared_buffer` .

Alors que le processeur finit par détecter cette prédiction, des effets secondaires résiduels peuvent être laissés dans le cache de l’UC qui révèlent des informations sur la valeur d’octet qui a été lue en dehors des limites de `buffer` . Ces effets secondaires peuvent être détectés par un contexte moins privilégié s’exécutant sur le système en détectant la rapidité d’accès à chaque ligne de cache `shared_buffer` . Les étapes à suivre pour y parvenir sont les suivantes :

1. **Appelez `ReadByte` plusieurs fois avec un nombre `untrusted_index` inférieur `buffer_size` à **. Le contexte d’attaque peut entraîner l’appel du contexte de la victime `ReadByte` (par exemple, via RPC) de telle sorte que le prédiction de branche soit formé comme étant `untrusted_index` inférieur à `buffer_size` .

2. **Videz toutes les lignes du `shared_buffer` cache dans **. Le contexte d’attaque doit vider toutes les lignes de cache dans la région partagée de mémoire référencée par `shared_buffer` . Étant donné que la région de la mémoire est partagée, cette opération est simple et peut être effectuée à l’aide d’intrinsèques tels que `_mm_clflush` .

3. **Invoke `ReadByte` avec `untrusted_index` valeur supérieure à `buffer_size` **. Le contexte d’attaque entraîne l’appel du contexte de la victime de `ReadByte` sorte qu’il prédit de manière incorrecte que la branche ne sera pas prise. Cela amène le processeur à exécuter de manière spéculative le corps du bloc If avec `untrusted_index` une valeur supérieure à `buffer_size` , ce qui aboutit à une lecture hors limites de `buffer` . Par conséquent, `shared_buffer` est indexé à l’aide d’une valeur potentiellement secrète qui a été lue en dehors des limites, provoquant ainsi le chargement de la ligne de cache correspondante par l’UC.

4. **Lisez chaque ligne de cache dans `shared_buffer` pour voir qui est accédé le plus rapidement**. Le contexte d’attaque peut lire chaque ligne de cache dans `shared_buffer` et détecter la ligne de cache qui se charge considérablement plus rapidement que les autres. Il s’agit de la ligne de cache susceptible d’être importée à l’étape 3. Étant donné qu’il y a une relation 1:1 entre la valeur d’octet et la ligne de cache dans cet exemple, cela permet à l’attaquant de déduire la valeur réelle de l’octet qui a été lu hors limites.

Les étapes ci-dessus fournissent un exemple d’utilisation d’une technique appelée FLUSH + Reload conjointement à l’exploitation d’une instance de CVE-2017-5753.

## <a name="what-software-scenarios-can-be-impacted"></a>Quels scénarios de logiciels peuvent être affectés ?

Le développement de logiciels sécurisés à l’aide d’un processus tel que le [cycle de vie de développement](https://www.microsoft.com/sdl/) de la sécurité (SDL) requiert généralement que les développeurs identifient les limites d’approbation qui existent dans leur application. Il existe une limite d’approbation dans les emplacements où une application peut interagir avec les données fournies par un contexte moins fiable, tel qu’un autre processus sur le système ou un processus de mode utilisateur non administratif dans le cas d’un pilote de périphérique en mode noyau. La nouvelle classe de vulnérabilités impliquant des canaux côté exécution spéculative s’applique à la plupart des limites d’approbation dans les modèles de sécurité logiciels existants qui isolent le code et les données sur un appareil.

Le tableau suivant fournit un résumé des modèles de sécurité logiciels dans lesquels les développeurs doivent se préoccuper de ces vulnérabilités :

|Limite de confiance|Description|
|----------------|----------------|
|Limite de machines virtuelles|Les applications qui isolent les charges de travail dans des machines virtuelles distinctes qui reçoivent des données non approuvées d’une autre machine virtuelle peuvent être menacées.|
|Limite du noyau|Un pilote de périphérique en mode noyau qui reçoit des données non approuvées à partir d’un processus de mode utilisateur non administratif peut être menacé.|
|Limite de processus|Une application qui reçoit des données non approuvées d’un autre processus s’exécutant sur le système local, par exemple par le biais d’un appel de procédure distante (RPC), d’une mémoire partagée ou d’autres mécanismes de communication entre processus (IPC) peut être menacée.|
|Limite de l’enclave|Une application qui s’exécute au sein d’une enclave sécurisée (par exemple Intel SGX) qui reçoit des données non approuvées en dehors de l’enclave peut être menacée.|
|Limite de langue|Une application qui interprète ou juste-à-temps (JIT) compile et exécute le code non fiable écrit dans un langage de niveau supérieur peut être menacé.|

Les applications qui ont une surface d’attaque exposée à l’une des limites d’approbation ci-dessus doivent examiner le code sur la surface d’attaque pour identifier et atténuer les instances possibles de vulnérabilités de canal côté exécution spéculative. Il convient de noter que les limites d’approbation exposées aux surfaces d’attaque à distance, telles que les protocoles de réseau distant, n’ont pas été démontrées comme étant à risque de vulnérabilités de canal côté exécution spéculative.

## <a name="potentially-vulnerable-coding-patterns"></a>Modèles de codage potentiellement vulnérables

Des vulnérabilités de canal côté exécution spéculative peuvent survenir en raison de plusieurs modèles de codage. Cette section décrit les modèles de codage potentiellement vulnérables et fournit des exemples pour chacun d’eux, mais il doit être reconnu que des variations sur ces thèmes peuvent exister. Par conséquent, les développeurs sont invités à prendre ces modèles comme exemples et non comme une liste exhaustive de tous les modèles de codage potentiellement vulnérables. Les mêmes classes de vulnérabilités de sécurité de la mémoire qui peuvent exister dans le logiciel aujourd’hui peuvent également exister en cas de chemins d’exécution spéculatifs et non ordonnés, notamment les dépassements de mémoire tampon, les accès aux tableaux hors limites, l’utilisation de la mémoire non initialisée, la confusion de type, etc. Les mêmes primitives que les attaquants peuvent utiliser pour exploiter les vulnérabilités de sécurité de la mémoire sur les chemins architecturaux peuvent également s’appliquer aux chemins spéculatifs.

En général, les canaux côté exécution spéculative liés à la prédiction de la branche conditionnelle peuvent survenir lorsqu’une expression conditionnelle opère sur des données qui peuvent être contrôlées ou influencées par un contexte de niveau de confiance moindre. Par exemple, cela peut inclure des expressions conditionnelles utilisées dans des **`if`** **`for`** instructions,,, **`while`** **`switch`** ou ternaires. Pour chacune de ces instructions, le compilateur peut générer une branche conditionnelle qui peut ensuite prédire la cible de la branche au moment de l’exécution.

Pour chaque exemple, un commentaire avec l’expression « barrière de SPÉCULation » est inséré, où un développeur peut introduire un cloisonnement comme atténuation. Ce sujet est abordé plus en détail dans la section relative aux atténuations.

## <a name="speculative-out-of-bounds-load"></a>Charge de non-limites spéculative

Cette catégorie de modèles de codage implique une prédiction incorrecte des branches conditionnelles qui entraîne un accès à la mémoire hors limites spéculative.

### <a name="array-out-of-bounds-load-feeding-a-load"></a>Chargement hors limites du tableau chargement d’une charge

Ce modèle de codage est le modèle de codage vulnérable décrit à l’origine pour CVE-2017-5753 (contournement du contrôle des limites). La section Background de cet article explique en détail ce modèle.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

De même, une charge hors limites de tableau peut se produire conjointement avec une boucle qui dépasse sa condition d’arrêt en raison d’une prédiction incorrecte. Dans cet exemple, la branche conditionnelle associée à l' `x < buffer_size` expression peut être à l’origine d’une prédiction et exécuter de manière spéculative le corps de la **`for`** boucle lorsque `x` est supérieur ou égal à `buffer_size` , ce qui entraîne une charge de non-limites spéculative.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[x];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Tableau des charges hors limites chargées d’alimenter une branche indirecte

Ce modèle de codage implique le cas où une prédiction de la branche conditionnelle peut aboutir à un accès hors limites à un tableau de pointeurs de fonction, qui mène ensuite à une branche indirecte vers l’adresse cible qui a été lue hors limites. L’extrait de code suivant fournit un exemple qui illustre cela.

Dans cet exemple, un identificateur de message non approuvé est fourni à DispatchMessage via le `untrusted_message_id` paramètre. Si `untrusted_message_id` est inférieur à `MAX_MESSAGE_ID` , il est utilisé pour indexer dans un tableau de pointeurs de fonction et créer une branche vers la cible de branche correspondante. Ce code est sécurisé de manière architecturale, mais si l’UC prédit la branche conditionnelle de manière incorrecte, cela peut entraîner `DispatchTable` une indexation par `untrusted_message_id` lorsque sa valeur est supérieure ou égale à `MAX_MESSAGE_ID` , ce qui aboutit à un accès hors limites. Cela peut entraîner une exécution spéculative à partir d’une adresse cible de branche qui est dérivée au-delà des limites du tableau, ce qui peut entraîner la divulgation d’informations en fonction du code exécuté de manière spéculative.

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    if (untrusted_message_id < MAX_MESSAGE_ID) {
        // SPECULATION BARRIER
        DispatchTable[untrusted_message_id](buffer, buffer_size);
    }
}
```

Comme dans le cas d’un tableau de charge hors limites chargée d’alimenter une autre charge, cette condition peut également se produire conjointement avec une boucle qui dépasse sa condition d’arrêt en raison d’une prédiction incorrecte.

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>Tableau des stockages hors limites alimentant une branche indirecte

Tandis que l’exemple précédent a montré comment une charge en dehors des limites peut influencer une cible de branche indirecte, il est également possible pour un magasin hors limites de modifier une cible de branche indirecte, telle qu’un pointeur de fonction ou une adresse de retour. Cela peut entraîner une exécution spéculative à partir d’une adresse spécifiée par une personne malveillante.

Dans cet exemple, un index non approuvé est passé via le `untrusted_index` paramètre. Si `untrusted_index` est inférieur au nombre d’éléments du `pointers` tableau (éléments 256), la valeur de pointeur fournie dans `ptr` est écrite dans le `pointers` tableau. Ce code est sécurisé de manière architecturale, mais si l’UC prédit la branche conditionnelle de manière incorrecte, cela peut entraîner une `ptr` écriture spéculative au-delà des limites du tableau alloué par la pile `pointers` . Cela peut entraîner une altération spéculative de l’adresse de retour pour `WriteSlot` . Si une personne malveillante peut contrôler la valeur de `ptr` , elle peut provoquer une exécution spéculative à partir d’une adresse arbitraire quand `WriteSlot` retourne le long du chemin spéculatif.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

De même, si une variable locale de pointeur de fonction nommée `func` a été allouée sur la pile, il peut être possible de modifier de manière spéculative l’adresse qui `func` fait référence à lorsque la prédiction de la branche conditionnelle se produit. Cela peut entraîner une exécution spéculative à partir d’une adresse arbitraire lorsque le pointeur de fonction est appelé par le biais de.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    void (*func)() = &callback;
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
    func();
}
```

Il convient de noter que ces deux exemples impliquent une modification spéculative des pointeurs de branche indirecte alloués par la pile. Il est possible que la modification spéculative puisse également se produire pour les variables globales, la mémoire allouée par tas et même la mémoire en lecture seule sur certains processeurs. Pour la mémoire allouée par la pile, le compilateur Microsoft C++ prend des mesures pour compliquer la modification spéculative des cibles de branche indirectes allouées par la pile, par exemple en réordonnant les variables locales de telle sorte que les tampons soient placés adjacents à un cookie de sécurité dans le cadre de la fonctionnalité de sécurité du compilateur [/GS](https://docs.microsoft.com/cpp/build/reference/gs-buffer-security-check) .

## <a name="speculative-type-confusion"></a>Confusion de type spéculatif

Cette catégorie concerne les modèles de codage qui peuvent donner lieu à une confusion de type spéculatif. Cela se produit en cas d’accès à la mémoire à l’aide d’un type incorrect sur un chemin d’accès non architectural au cours de l’exécution spéculative. La prédiction de la branche conditionnelle et le contournement spéculatif du magasin peuvent potentiellement entraîner une confusion de type spéculaire.

Pour le contournement spéculatif des magasins, cela peut se produire dans les scénarios où un compilateur réutilise un emplacement de pile pour les variables de plusieurs types. Cela est dû au fait que le magasin architectural d’une variable de type `A` peut être contourné, ce qui permet à la charge de type de `A` s’exécuter de manière spéculative avant que la variable ne soit assignée. Si la variable précédemment stockée est d’un type différent, cela peut créer les conditions pour une confusion de type spéculatif.

Pour une prédiction incorrecte de la branche conditionnelle, l’extrait de code suivant est utilisé pour décrire les différentes conditions auxquelles la confusion de type spéculatif peut donner lieu.

```cpp
enum TypeName {
    Type1,
    Type2
};

class CBaseType {
public:
    CBaseType(TypeName type) : type(type) {}
    TypeName type;
};

class CType1 : public CBaseType {
public:
    CType1() : CBaseType(Type1) {}
    char field1[256];
    unsigned char field2;
};

class CType2 : public CBaseType {
public:
    CType2() : CBaseType(Type2) {}
    void (*dispatch_routine)();
    unsigned char field2;
};

// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ProcessType(CBaseType *obj)
{
    if (obj->type == Type1) {
        // SPECULATION BARRIER
        CType1 *obj1 = static_cast<CType1 *>(obj);

        unsigned char value = obj1->field2;

        return shared_buffer[value * 4096];
    }
    else if (obj->type == Type2) {
        // SPECULATION BARRIER
        CType2 *obj2 = static_cast<CType2 *>(obj);

        obj2->dispatch_routine();

        return obj2->field2;
    }
}
```

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Confusion de type spéculatif conduisant à une charge hors limites

Ce modèle de codage implique le cas où une confusion de type spéculatif peut entraîner un accès aux champs hors limites ou de type confus, où la valeur chargée alimente une adresse de chargement suivante. Cela est similaire au modèle de codage hors limites du tableau, mais il est présenté dans une autre séquence de codage, comme indiqué ci-dessus. Dans cet exemple, un contexte d’attaque peut entraîner l’exécution de plusieurs fois le contexte de la victime `ProcessType` avec un objet de type `CType1` (le `type` champ est égal à `Type1` ). Cela aura pour effet d’effectuer l’apprentissage de la branche conditionnelle pour la première **`if`** instruction à prédire non prise. Le contexte d’attaque peut alors entraîner l’exécution du contexte de la victime `ProcessType` avec un objet de type `CType2` . Cela peut entraîner une confusion spéculative si la branche conditionnelle de la première **`if`** instruction prédit et exécute le corps de l' **`if`** instruction, castant ainsi un objet de type `CType2` en `CType1` . Étant donné que est inférieur à `CType2` `CType1` , l’accès à la mémoire à entraîne `CType1::field2` une charge de données hors limites spéculative qui peut être secrète. Cette valeur est ensuite utilisée dans une charge à partir de `shared_buffer` laquelle peut créer des effets secondaires observables, comme avec l’exemple de hors limites de tableau décrit précédemment.

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Confusion de type spéculatif conduisant à une branche indirecte

Ce modèle de codage implique le cas où une confusion de type spéculatif peut entraîner une branche indirecte non sécurisée lors de l’exécution spéculative. Dans cet exemple, un contexte d’attaque peut entraîner l’exécution de plusieurs fois le contexte de la victime `ProcessType` avec un objet de type `CType2` (le `type` champ est égal à `Type2` ). Cela aura pour effet d’effectuer l’apprentissage de la branche conditionnelle pour la première **`if`** instruction et l' `else if` instruction à ne pas prendre en compte. Le contexte d’attaque peut alors entraîner l’exécution du contexte de la victime `ProcessType` avec un objet de type `CType1` . Cela peut entraîner une confusion de type spéculaire si la branche conditionnelle de la première **`if`** instruction prédit et que l' `else if` instruction prédit non effectuée, en exécutant ainsi le corps du `else if` et en convertissant un objet de type `CType1` en `CType2` . Étant donné que le `CType2::dispatch_routine` champ chevauche le **`char`** tableau `CType1::field1` , cela peut entraîner une branche indirecte spéculative sur une cible de branche inattendue. Si le contexte d’attaque peut contrôler les valeurs d’octets dans le `CType1::field1` tableau, il peut être en mesure de contrôler l’adresse cible de la branche.

## <a name="speculative-uninitialized-use"></a>Utilisation spéculative non initialisée

Cette catégorie de modèles de codage implique des scénarios dans lesquels l’exécution spéculative peut accéder à la mémoire non initialisée et l’utiliser pour alimenter une branche de charge ou indirecte ultérieure. Pour que ces modèles de codage soient exploitables, un attaquant doit être en mesure de contrôler ou d’influencer significativement le contenu de la mémoire utilisée sans être initialisé par le contexte dans lequel il est utilisé.

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>Utilisation spéculative non initialisée conduisant à une charge hors limites

Une utilisation spéculative non initialisée peut potentiellement entraîner une charge hors limites à l’aide d’une valeur contrôlée par un attaquant. Dans l’exemple ci-dessous, la valeur de `index` est assignée `trusted_index` sur tous les chemins d’accès de l’architecture et `trusted_index` est supposée être inférieure ou égale à `buffer_size` . Toutefois, en fonction du code produit par le compilateur, il est possible qu’un contournement spéculatif du magasin puisse se produire, ce qui permet à la charge à partir des `buffer[index]` expressions dépendantes de s’exécuter avant l’assignation à `index` . Dans ce cas, une valeur non initialisée pour `index` sera utilisée comme décalage dans `buffer` qui pourrait permettre à une personne malveillante de lire les informations sensibles hors limites et de les transmettre via un canal latéral via la charge dépendante de `shared_buffer` .

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

void InitializeIndex(unsigned int trusted_index, unsigned int *index) {
    *index = trusted_index;
}

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int trusted_index) {
    unsigned int index;

    InitializeIndex(trusted_index, &index); // not inlined

    // SPECULATION BARRIER
    unsigned char value = buffer[index];
    return shared_buffer[value * 4096];
}
```

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>Utilisation spéculative non initialisée conduisant à une branche indirecte

Une utilisation spéculative non initialisée peut potentiellement aboutir à une branche indirecte dans laquelle la cible de branche est contrôlée par une personne malveillante. Dans l’exemple ci-dessous, `routine` est assigné à `DefaultMessageRoutine1` ou `DefaultMessageRoutine` en fonction de la valeur `mode` de. Sur le chemin architectural, cela se traduira `routine` toujours par une initialisation en avance de la branche indirecte. Toutefois, en fonction du code produit par le compilateur, un contournement spéculatif du magasin peut se produire, ce qui permet à la branche indirecte `routine` d’être exécutée de manière spéculative avant l’assignation à `routine` . Dans ce cas, une personne malveillante peut être en mesure de s’exécuter de façon spéculative à partir d’une adresse arbitraire, en supposant que l’attaquant peut influencer ou contrôler la valeur non initialisée de `routine` .

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];
extern unsigned int mode;

void InitializeRoutine(MESSAGE_ROUTINE *routine) {
    if (mode == 1) {
        *routine = &DefaultMessageRoutine1;
    }
    else {
        *routine = &DefaultMessageRoutine;
    }
}

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    MESSAGE_ROUTINE routine;

    InitializeRoutine(&routine); // not inlined

    // SPECULATION BARRIER
    routine(buffer, buffer_size);
}
```

## <a name="mitigation-options"></a>Options de correction

Les vulnérabilités de canal côté exécution spéculative peuvent être atténuées en apportant des modifications au code source. Ces modifications peuvent impliquer l’atténuation des instances spécifiques d’une vulnérabilité, telles que l’ajout d’une *barrière de spéculation*ou l’apport de modifications à la conception d’une application pour rendre des informations sensibles inaccessibles à l’exécution spéculative.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Barrière de spéculation via l’instrumentation manuelle

Une *barrière de spéculation* peut être insérée manuellement par un développeur pour empêcher l’exécution spéculative de continuer avec un chemin d’accès non architectural. Par exemple, un développeur peut insérer une barrière de spéculation avant un modèle de codage dangereux dans le corps d’un bloc conditionnel, soit au début du bloc (après la branche conditionnelle), soit avant le premier chargement qui est à l’origine du problème. Cela empêchera une prédiction incorrecte de la branche conditionnelle d’exécuter le code dangereux sur un chemin d’accès non architectural en sérialisant l’exécution. La séquence de barrière de spéculation diffère selon l’architecture matérielle, comme décrit dans le tableau suivant :

|Architecture|Fonction de barrière de spéculation pour CVE-2017-5753|Fonction de barrière de spéculation pour CVE-2018-3639|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence ()|_mm_lfence ()|
|ARM|actuellement non disponible|__dsb (0)|
|ARM64|actuellement non disponible|__dsb (0)|

Par exemple, le modèle de code suivant peut être atténué à l’aide de l' `_mm_lfence` intrinsèque, comme indiqué ci-dessous.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        _mm_lfence();
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Barrière de spéculation via l’instrumentation au moment du compilateur

Le compilateur Microsoft C++ dans Visual Studio 2017 (à partir de la version 15.5.5) prend en charge le `/Qspectre` commutateur qui insère automatiquement une barrière de spéculation pour un ensemble limité de modèles de codage potentiellement vulnérables liés à CVE-2017-5753. La documentation de l’indicateur [/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre) fournit plus d’informations sur ses effets et son utilisation. Il est important de noter que cet indicateur ne couvre pas tous les modèles de codage potentiellement vulnérables et que les développeurs ne doivent pas s’en servir comme solution de contournement complète pour cette classe de vulnérabilités.

### <a name="masking-array-indices"></a>Masquage d’index de tableau

Dans les cas où une charge de non-limites spéculative peut se produire, l’index de tableau peut être fortement limité à la fois sur le chemin d’accès architectural et non architectural en ajoutant la logique à la liaison explicite de l’index de tableau. Par exemple, si un tableau peut être alloué à une taille qui est alignée sur une puissance de deux, un masque simple peut être introduit. Cela est illustré dans l’exemple ci-dessous, où il est supposé qu’il `buffer_size` est aligné sur une puissance de deux. Cela garantit que `untrusted_index` est toujours inférieur à `buffer_size` , même si une prédiction incorrecte de la branche conditionnelle se produit et `untrusted_index` a été passée avec une valeur supérieure ou égale à `buffer_size` .

Il convient de noter que le masquage de l’index effectué ici pourrait faire l’objet d’un contournement spéculatif du magasin en fonction du code généré par le compilateur.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        untrusted_index &= (buffer_size - 1);
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="removing-sensitive-information-from-memory"></a>Suppression d’informations sensibles de la mémoire

Une autre technique qui peut être utilisée pour atténuer les vulnérabilités de canal côté exécution spéculative consiste à supprimer les informations sensibles de la mémoire. Les développeurs de logiciels peuvent rechercher des opportunités de refactoriser leur application de telle sorte que les informations sensibles ne soient pas accessibles lors de l’exécution spéculative. Pour ce faire, vous pouvez refactoriser la conception d’une application afin d’isoler les informations sensibles dans des processus distincts. Par exemple, une application de navigateur Web peut tenter d’isoler les données associées à chaque origine Web dans des processus distincts, empêchant ainsi un processus d’accéder aux données Cross-Origin par le biais d’une exécution spéculative.

## <a name="see-also"></a>Voir aussi

[Conseils pour atténuer les vulnérabilités du canal latéral de l’exécution spéculative](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[Atténuation des vulnérabilités matérielles du canal côté exécution spéculative](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
