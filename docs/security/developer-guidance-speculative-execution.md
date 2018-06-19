---
title: Guide du développeur de C++ pour les canaux côté exécution spéculatif | Documents Microsoft
ms.custom: ''
ms.date: 05/21/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
author: mamillmsft
ms.author: mikeblome
ms.workload:
- cplusplus
ms.openlocfilehash: 515e2223e67d86da12488d9880a1a0a258fc4bdf
ms.sourcegitcommit: 4b2c3b0c720aef42bce7e1e5566723b0fec5ec7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34428708"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>Guide du développeur de C++ pour les canaux côté spéculatif d’exécution

Cet article contient des conseils pour les développeurs pour vous aider à identifier et de limiter les exécution spéculative côté canal matériel des vulnérabilités dans les logiciels de C++. Ces vulnérabilités peuvent divulguer des informations sensibles au-delà des limites de confiance et peuvent affecter le logiciel qui s’exécute sur les processeurs qui prennent en charge spéculative, non ordonnés de l’exécution d’instructions. Cette classe de vulnérabilités premier décrites dans janvier, 2018 et des informations supplémentaires et vous trouverez des instructions dans [avis de sécurité de Microsoft](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002).

Les instructions fournies dans cet article sont liée aux classes de vulnérabilités représentées par :

1. CVE-2017-5753, également appelé Spectre de type variant 1. Cette classe de vulnérabilité de matériel est liée aux canaux côté qui peuvent survenir en raison d’une exécution spéculative qui se produit suite à une mauvaise prédiction de branche conditionnelle. Le compilateur Visual C++ dans Visual Studio 2017 (à partir de la version 15.5.5) prend en charge la `/Qspectre` commutateur qui permet également une limitation de la compilation pour un ensemble limité de modèles de codage potentiellement vulnérables liés à CVE-2017-5753. La documentation relative à la [/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre) indicateur fournit plus d’informations sur l’utilisation et ses effets.

2. CVE-2018-3639, également appelé [spéculatif magasin contournement (SSB)](https://aka.ms/sescsrdssb). Cette classe de vulnérabilité de matériel est liée aux canaux côté qui peuvent survenir en raison d’une exécution spéculative d’une charge avance un magasin dépendant à la suite d’une mauvaise prédiction de l’accès mémoire.

Vous trouverez une introduction accessible aux vulnérabilités de canal côté spéculatif d’exécution dans la présentation intitulée [le cas du Spectre et Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) par une des équipes de recherche qui a découvert ces problèmes.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>Quelles sont les vulnérabilités de matériel spéculatif d’exécution côté canal ?

Unités centrales modernes offre un degré de performances en permettant l’utilisation de spéculative et ordre de l’exécution d’instructions. Par exemple, il suffit souvent prédiction de la cible des branches (conditionnels et indirectes) qui permet à l’UC commencer suit l’exécution des instructions sur la cible de branche prédite, évitant ainsi un blocage jusqu'à ce que la cible de branche réel est résolu. Dans le cas où le processeur détecte ultérieurement qu’une mauvaise prédiction s’est produite, ensemble de l’état de l’ordinateur qui a été calculé spéculative est ignoré. Cela garantit qu’il n’y a aucun effet visible une architecture de la spéculation mal prédites retirée.

Pendant l’exécution spéculative n’affecte pas l’état de visibilité de point de vue architectural, il peut laisser des traces résiduelles dans état-architecturaux, tels que les caches différents qui sont utilisées par l’UC. Il s’agit de ces traces résiduelles spéculatif d’exécution qui peut donner lieu à des vulnérabilités de canal côté. Pour mieux comprendre, examinons le fragment de code suivant qui fournit un exemple de CVE-2017-5753 (limites vérifier contournement)

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

Dans cet exemple, `ReadByte` est fourni une mémoire tampon, une taille de mémoire tampon et un index dans le tampon. Le paramètre d’index, tel que spécifié par `untrusted_index`, est fourni par un inférieur contexte privilégié, par exemple un processus non administratifs. Si `untrusted_index` est inférieure à `buffer_size`, puis le caractère situé à cet index est en lecture à partir de `buffer` et utilisé pour l’index dans une région partagée de la mémoire référencée par `shared_buffer`. 

À partir d’un point de vue architectural, cette séquence de code ne présente aucun risque car il est garanti que `untrusted_index` sera toujours inférieur à `buffer_size`. Toutefois, en présence d’une exécution spéculative, il est possible que le processeur sera mispredict la branche conditionnelle et exécuter le corps de la s’instruction même lorsque `untrusted_index` est supérieur ou égal à `buffer_size`. Par conséquent, le processeur peut lire spéculative d’un octet au-delà des limites de `buffer` (qui peut être une clé secrète) et vous pouvez ensuite utiliser cette valeur d’octet pour calculer l’adresse d’un chargement ultérieur via `shared_buffer`. 

Alors que l’UC finalement détecte cette mauvaise prédiction, des effets secondaires qui sont restées peut rester dans le cache de processeur qui révèlent des informations sur la valeur d’octet qui a été lu en dehors des limites de `buffer`. Ces effets peuvent être détectées par un inférieur contexte privilégié en cours d’exécution sur le système par la détection de la rapidité avec laquelle chaque cache ligne `shared_buffer` est accessible. Les étapes qui peuvent être prises pour effectuer cette opération sont :

1. **Appeler `ReadByte` plusieurs fois avec `untrusted_index` qui est inférieur à `buffer_size`** . Le contexte qui peut entraîner le contexte de la victime appeler `ReadByte` (par exemple via RPC) dont le PRÉDICTEUR de branche est formé pour être effectuée n’est ne pas en tant que `untrusted_index` est inférieure à `buffer_size`.

2. **Vider toutes les lignes de cache de `shared_buffer`** . Le contexte qui doit vider toutes les lignes du cache dans la région partagée de la mémoire référencée par `shared_buffer`. Étant donné que la région de mémoire est partagée, il est simple et peut être effectuée à l’aide des fonctions intrinsèques tels que `_mm_clflush`.

3. **Appeler `ReadByte` avec `untrusted_index` est supérieur à `buffer_size`** . Le contexte qui provoque le contexte de la victime appeler `ReadByte` où elle prédit correctement que la branche n’est pas prise. Cela entraîne le processeur spéculative exécuter le corps de la se bloc avec `untrusted_index` est supérieur à `buffer_size`, par conséquent, conduisant à une lecture hors limites de `buffer`. Par conséquent, `shared_buffer` est indexée à l’aide d’une valeur potentiellement secrète qui a été lu hors limites, ce qui entraîne la ligne de cache correspondante doit être chargée par l’UC.

4. **Lire chaque ligne du cache `shared_buffer` pour voir ce qui se trouve plus rapidement**. Le contexte qui peut lire chaque ligne de cache dans `shared_buffer` et détecter la ligne de cache qui charge beaucoup plus rapidement que les autres. Il s’agit de la ligne de cache est susceptible d’avoir été introduits par l’étape 3. Dans la mesure où il existe une relation 1:1 entre la ligne de valeur et le cache des octets dans cet exemple, cela permet la personne malveillante déduire la valeur réelle de l’octet qui a été lu hors limites.

Les étapes ci-dessus fournissent un exemple d’utilisation d’une technique appelée vidage + recharger conjointement avec une instance de CVE-2017-5753 l’exploitation.

## <a name="what-software-scenarios-can-be-impacted"></a>Les scénarios de logiciel peuvent être affectées ?

Développement de logiciels sécurisés à l’aide d’un processus tel que le [cycle de développement sécurité](https://www.microsoft.com/en-us/sdl/) (SDL) requiert en général, les développeurs identifier les limites d’approbation qui existent dans leur application. Il existe une limite d’approbation dans les emplacements où une application peut interagir avec les données fournies par un contexte de confiance moindre, comme un autre processus sur le système ou un processus de mode utilisateur non administratif dans le cas d’un pilote de périphérique en mode noyau. La nouvelle classe de vulnérabilités impliquant des canaux du côté exécution spéculative ne s’applique à la plupart des limites de confiance dans les modèles de sécurité logiciels existants qui isolent le code et les données sur un appareil. 

Le tableau suivant fournit un résumé des modèles de sécurité logiciels où les développeurs doivent se soucier de ces problèmes de sécurité qui se produisent :

|Limite d’approbation|Description|
|----------------|----------------|
|Limite de l’ordinateur virtuel|Les applications qui isolent les charges de travail dans des machines virtuelles distinctes qui reçoivent des données non fiables à partir d’un autre ordinateur virtuel peuvent être exposés.| 
|Limite du noyau|Un pilote de périphérique en mode noyau qui reçoit des données non fiables à partir d’un processus de mode utilisateur non-administrateur courent un risque.| 
|Limite de processus|Une application qui reçoit des données non fiables à partir d’un autre processus en cours d’exécution sur le système local, telles que via un appel de procédure distante (RPC), de mémoire partagée ou d’autres communications entre processus (IPC) mécanismes courent un risque.|
|Limite de enclave|Une application qui s’exécute dans un enclave sécurisé (par exemple, Intel SGX) qui reçoit des données non approuvées provenant en dehors de l’enclave peut être menacé.|
|Limite de langage|Une application qui interprète ou un juste à temps (JIT) compile et exécute le code non fiable écrit un langage de niveau supérieur peut être compromise.|

Applications qui ont surface d’attaque exposée à un des éléments ci-dessus confiance limites doivent examiner le code sur la surface d’attaque pour identifier et limiter les occurrences possibles de vulnérabilités de canal côté spéculatif d’exécution. Il convient de noter qu’exposés à des surfaces d’attaque à distance, telles que les protocoles réseau à distance, des limites d’approbation n'ont pas démontrés courent un risque aux vulnérabilités de canal côté spéculatif d’exécution.

## <a name="potentially-vulnerable-coding-patterns"></a>Modèles de codage potentiellement vulnérables

Vulnérabilités de canal côté spéculatif d’exécution peuvent se produire en raison de plusieurs modèles de codage. Cette section décrit les modèles de codage potentiellement vulnérables et fournit des exemples pour chaque, mais il doit être reconnu que les variations sur ces thèmes peuvent exister. Par conséquent, les développeurs nous recommandons de prendre ces modèles comme exemples et non comme une liste exhaustive de tous les modèles de codage potentiellement vulnérables.

En règle générale, mauvaise prédiction de l’exécution spéculatif côté canaux connexes Conditional branche peut se produire lorsqu’une expression conditionnelle fonctionne sur les données qui peuvent être contrôlées ou influencées par un contexte de confiance moindre. Par exemple, cela peut inclure des expressions conditionnelles utilisées dans `if`, `for`, `while`, `switch`, ou les instructions ternaires. Pour chacune de ces instructions, le compilateur peut générer une branche conditionnelle l’UC peut alors prévoir de la cible de branche pour lors de l’exécution.

Pour chaque exemple, un commentaire avec la phrase « Spéculation barrière » est inséré dans lequel un développeur peut introduire une barrière pour atténuer le problème. Ce sujet est abordé plus en détail dans la section sur les solutions d’atténuation.

## <a name="speculative-out-of-bounds-load"></a>Chargement de spéculatif hors limites

Cette catégorie de modèles de codage implique une mauvaise prédiction de branche conditionnelle qui entraîne un spéculatif hors limites accès à la mémoire.

### <a name="array-out-of-bounds-load-feeding-a-load"></a>Une charge de l’alimentation de charge de tableau hors limites

Ce modèle de codage est le modèle de codage vulnérable décrit à l’origine pour CVE-2017-5753 (limites vérifier contournement). La section de l’arrière-plan de cet article explique ce modèle en détail.

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

De même, un tableau hors limites charge peut se produire en conjonction avec une boucle qui dépasse la fin d’exécution de condition en raison d’une mauvaise prédiction. Dans cet exemple, la branche conditionnelle associé à la `x < buffer_size` expression peut mispredict et spéculative exécuter le corps de la `for` boucle lorsque `x` est supérieur ou égal à `buffer_size`, par conséquent, se traduisant par un spéculatif charger le hors limites.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Tableau hors limites charger une branche indirecte de l’alimentation

Ce modèle de codage implique le cas où une mauvaise prédiction de branche conditionnelle peut entraîner un dépassement accès à un tableau de pointeurs de fonction qui entraîne une branche indirecte à la cible puis adresse qui a été lu hors limites. L’extrait de code suivant fournit un exemple qui illustre cette méthode. 

Dans cet exemple, un identificateur de message non approuvé est fourni à DispatchMessage via le `untrusted_message_id` paramètre. Si `untrusted_message_id` est inférieure à `MAX_MESSAGE_ID`, il est utilisé pour indexer dans un tableau de pointeurs de fonction et créer une branche vers la cible de branche correspondante. Ce code est une architecture sécurisé, mais si l’UC prédictions incorrectes de branches la branche conditionnelle, il peut entraîner `DispatchTable` indexé par `untrusted_message_id` lorsque sa valeur est supérieure ou égale à `MAX_MESSAGE_ID`, par conséquent, ce qui entraîne un accès hors limites. Cela peut entraîner une exécution spéculative à partir d’une adresse de cible de branche est dérivée au-delà des limites du tableau, ce qui peut entraîner une divulgation d’informations en fonction du code qui est exécuté de manière spéculative.

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

Comme avec le cas d’un tableau hors limites charger un autre charge de l’alimentation, cette condition peut également survenir conjointement avec une boucle qui dépasse sa condition d’arrêt en raison d’une mauvaise prédiction.

## <a name="speculative-type-confusion"></a>Confusion entre types spéculatif

Cette catégorie porte sur les modèles qui peuvent donner lieu à une confusion spéculatif type de codage. Cela se produit lorsque la mémoire est accessible à l’aide d’un type incorrect le long d’un chemin d’accès-architecturaux pendant l’exécution spéculative. Mauvaise prédiction de branche conditionnelle et magasin spéculatif contournement susceptibles d’entraîner une confusion type spéculatif. 

Contournement de la banque spéculatif, cela peut se produire dans les scénarios où un compilateur réutilise un emplacement de pile pour les variables de plusieurs types. C’est parce que le magasin d’architecture d’une variable de type `A` peuvent être ignorés, permettant ainsi la charge de type `A` spéculative exécuter avant que la variable est assignée. Si la variable précédemment stockée est d’un type différent, cela peut créer les conditions d’une confusion type spéculatif.

Pour une mauvaise prédiction de branche conditionnelle, l’extrait de code suivant se servira à décrire différentes conditions confusion entre types spéculatif peut donner lieu à.

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

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Confusion type spéculatif conduisant à une charge hors limites

Ce modèle de codage implique le cas où une confusion type spéculatif peut entraîner un dépassement ou accès vous ne comprenez pas le type de champ où les flux de valeur chargée une adresse de chargement ultérieur. Cela est similaire au modèle de codage hors limites de tableau, mais il est identifié par une alternative de codage séquence comme indiqué ci-dessus. Dans cet exemple, un contexte qui peut entraîner le contexte de la victime d’exécution `ProcessType` plusieurs fois avec un objet de type `CType1` (`type` champ est égal à `Type1`). Cela aura pour effet de l’apprentissage de la branche conditionnelle pour la première `if` instruction pour ne prédire pas effectuée. Le contexte qui peut provoquer ensuite le contexte de la victime d’exécution `ProcessType` avec un objet de type `CType2`. Cela peut entraîner une confusion spéculatif type si l’attribut conditional créez une branche pour la première `if` instruction prédictions incorrectes de branches et exécute le corps de la `if` instruction, par conséquent, effectuer un cast d’un objet de type `CType2` à `CType1`. Étant donné que `CType2` est inférieure à `CType1`, l’accès à la mémoire à `CType1::field2` résultat dans un spéculatif se chargera hors limites de données qui peuvent être secret principal. Cette valeur est ensuite utilisée dans une charge de `shared_buffer` qui peut créer des effets secondaires observables, comme avec le tableau hors limites exemple décrit précédemment.

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Confusion type spéculatif conduisant à une branche indirecte

Ce modèle de codage implique le cas où une confusion type spéculatif peut entraîner une branche indirecte unsafe au cours d’exécution spéculative. Dans cet exemple, un contexte qui peut entraîner le contexte de la victime d’exécution `ProcessType` plusieurs fois avec un objet de type `CType2` (`type` champ est égal à `Type2`). Cela aura pour effet de l’apprentissage de la branche conditionnelle pour la première `if` instruction à prendre et `else if` instruction à entreprendre ne pas. Le contexte qui peut provoquer ensuite le contexte de la victime d’exécution `ProcessType` avec un objet de type `CType1`. Cela peut entraîner une confusion spéculatif type si l’attribut conditional créez une branche pour la première `if` instruction prédit prises et `else if` instruction ne prédit pas effectuée, par conséquent, l’exécution du corps de la `else if` et de la conversion d’un objet de type `CType1` à `CType2`. Étant donné que la `CType2::dispatch_routine` champ chevauche le `char` tableau `CType1::field1`, cela peut entraîner une branche indirecte spéculative à une cible de branche involontaire. Si le contexte qui permettre contrôler les valeurs d’octets dans le `CType1::field1` tableau, ils ne peuvent être en mesure de contrôler l’adresse cible de branche.

## <a name="speculative-uninitialized-use"></a>Utilisation non initialisée spéculative

Cette catégorie de modèles de codage implique des scénarios dans lesquels exécution spéculative peut accéder à la mémoire non initialisée et l’utiliser pour alimenter un chargement ultérieur ou une branche indirecte. Pour ces modèles de codage être exploitable, un attaquant doit être en mesure de contrôle ou de manière significative influencent le contenu de la mémoire qui est utilisé sans être initialisé par le contexte utilisé dans.

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>Spéculative utilisation sans être initialisé à l’origine d’une charge hors limites

Une utilisation sans être initialisé spéculative susceptibles d’entraîner un hors limites de charge à l’aide d’une valeur contrôlé par l’attaquant. Dans l’exemple ci-dessous, la valeur de `index` est attribué `trusted_index` sur tous les chemins d’architecture et `trusted_index` est supposé pour être inférieur ou égal à `buffer_size`. Toutefois, en fonction du code généré par le compilateur, il est possible qu’un contournement spéculatif magasin peut-être se produire et qui permet de la charge de `buffer[index]` et les expressions dépendantes à exécuter avant l’assignation à `index`. Si cela se produit, une valeur non initialisée pour `index` sera utilisé comme un offset dans `buffer` qui permettrait à un attaquant de lire des informations sensibles hors limites et cela communiquent via un canal côté via le chargement dépendant de `shared_buffer` .

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

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>Spéculative utilisation sans être initialisé à l’origine d’une branche indirecte

Une utilisation sans être initialisé spéculative susceptibles d’entraîner une branche indirecte où la cible de branche est contrôlée par une personne malveillante. Dans l’exemple ci-dessous, `routine` est affectée à une `DefaultMessageRoutine1` ou `DefaultMessageRoutine` selon la valeur de `mode`. Sur le chemin d’accès architectural, il en résulte `routine` toujours en cours d’initialisation avant la branche indirecte. Toutefois, en fonction du code généré par le compilateur, un contournement spéculatif magasin peut se produire qui permet la branche indirecte via `routine` à exécuter avant l’assignation à spéculative `routine`. Si cela se produit, une personne malveillante peut être en mesure d’exécuter suit à partir d’une adresse arbitraire, en supposant que la personne malveillante peut influencer ou contrôler la valeur non initialisée de `routine`.

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

## <a name="mitigation-options"></a>Options d’atténuation

Des vulnérabilités de l’exécution spéculatif côté canal peuvent être atténuées en apportant des modifications au code source. Ces modifications peuvent impliquer d’atténuation des instances spécifiques d’une vulnérabilité, comme en ajoutant un *barrière de spéculation*, ou en apportant des modifications à la conception d’une application afin que les informations sensibles ne spéculatif exécution.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Cloisonnement spéculation via l’instrumentation manuelle

A *barrière de spéculation* peut être insérée manuellement par un développeur pour empêcher l’exécution de spéculative à partir de continuer le long d’un chemin d’accès non architecturales. Par exemple, un développeur peut insérer une barrière spéculation avant un modèle de codage dangereuse dans le corps d’un bloc conditionnel, soit au début du bloc (après la branche conditionnelle) ou avant le premier chargement pose un problème. Cela empêche une mauvaise prédiction de branche conditionnelle de l’exécution du code dangereux sur un chemin d’accès-architecturaux en sérialisant l’exécution. La séquence de barrière spéculation diffère par l’architecture matérielle, comme décrit dans le tableau suivant :

|Architecture|Cloisonnement spéculation intrinsèque pour CVE-2017-5753|Cloisonnement spéculation intrinsèque pour CVE-2018-3639|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence()|_mm_lfence()|
|ARM|N’est pas disponible|__dsb(0)|
|ARM64|N’est pas disponible|__dsb(0)|

Par exemple, le modèle de code suivant peut être atténué à l’aide de la `_mm_lfence` intrinsèque, comme indiqué ci-dessous.

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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Cloisonnement spéculation par l’intermédiaire du compilateur au moment instrumentation

Le compilateur Visual C++ dans Visual Studio 2017 (à partir de la version 15.5.5) prend en charge la `/Qspectre` commutateur qui insère automatiquement une barrière spéculation pour un ensemble limité de modèles de codage potentiellement vulnérables liés à CVE-2017-5753. La documentation relative à la [/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre) indicateur fournit plus d’informations sur l’utilisation et ses effets. Il est important de noter que cet indicateur ne couvre pas tous les modèles de codage potentiellement vulnérables et par conséquent les développeurs fiez pas à elle pour atténuer le problème complet pour cette classe de vulnérabilités.

## <a name="masking-array-indices"></a>Masquage des indices de tableau

Dans les cas où un spéculatif hors limites de charge peut se produire, l’index de tableau peut être fortement limitée sur le chemin-architecturaux et d’architecture en ajoutant une logique pour lié explicitement l’index de tableau. Par exemple, si un tableau peut être affecté à une taille qui est alignée à une puissance de deux, puis un masque simple peut être introduit. Ceci est illustré dans l’exemple ci-dessous, où il est supposé que `buffer_size` est alignée à une puissance de deux. Cela garantit que `untrusted_index` est toujours inférieure à `buffer_size`, même en cas d’une mauvaise prédiction de branche conditionnelle et `untrusted_index` a été passé avec une valeur supérieure ou égale à `buffer_size`.

Il convient de noter que le masquage de l’index effectué ici peut être soumise à ignorer spéculatif magasin en fonction du code généré par le compilateur.

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

## <a name="removing-sensitive-information-from-memory"></a>Suppression des informations sensibles de la mémoire

Une autre technique qui peut être utilisée pour atténuer les vulnérabilités de canal côté exécution spéculative consiste à supprimer les informations sensibles de la mémoire. Les développeurs de logiciels peuvent rechercher les opportunités de refactoriser leur application, telles que des informations sensibles ne sont pas accessibles pendant l’exécution spéculative. Cela peut être accompli en refactorisant la conception d’une application pour isoler les informations sensibles dans des processus distincts. Par exemple, une application de navigateur web peut tenter d’isoler les données associées à chaque origine web dans des processus distincts, empêchant ainsi un processus en mesure d’accéder aux données de cross-origine via l’exécution spéculative.

## <a name="see-also"></a>Voir aussi

[Conseils pour limiter les vulnérabilités de canal latéral exécution spéculative](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)
[limiter les vulnérabilités de matériel exécution spéculative côté canal](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)