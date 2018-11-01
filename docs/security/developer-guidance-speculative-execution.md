---
title: Guide du développeur de C++ pour les canaux du côté l’exécution spéculative
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: 94e55f08e4ff427aef0c93bf74c711a6fd935d0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631023"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>Guide du développeur de C++ pour les canaux du côté l’exécution spéculative

Cet article contient des conseils pour les développeurs aider à identifier et atténuer les vulnérabilités de matériel de canal de côté l’exécution spéculative dans des logiciels de C++. Ces vulnérabilités peuvent divulguer des informations sensibles au-delà des limites de confiance et peuvent affecter les logiciels qui s’exécutent sur des processeurs qui prennent en charge l’exécution spéculative et de désordre des instructions. Cette classe de vulnérabilités a été premier décrit dans janvier 2018 et arrière-plan supplémentaire et vous trouverez des instructions dans [avis de sécurité de Microsoft](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002).

Les instructions fournies par cet article concerne les classes de vulnérabilités représentées par :

1. CVE-2017-5753, également connu sous le variante Spectre 1. Cette classe de vulnérabilité de matériel est liée à des canaux du côté qui peuvent se produire en raison de l’exécution spéculative qui se produit suite à une mauvaise prédiction de branchement conditionnel. Le compilateur Visual C++ dans Visual Studio 2017 (à partir de la version 15.5.5) prend en charge la `/Qspectre` commutateur qui fournit une atténuation de la compilation pour un ensemble limité de modèles de codage potentiellement vulnérables liés à CVE-2017-5753. Le `/Qspectre` commutateur est également disponible dans Visual Studio 2015 Update 3 via [Ko 4338871](https://support.microsoft.com/help/4338871). La documentation relative à la [/qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre) indicateur fournit plus d’informations sur l’utilisation et ses effets.

2. CVE-2018-3639, également appelé [spéculative Store contournement (SSB)](https://aka.ms/sescsrdssb). Cette classe de vulnérabilité de matériel est liée à des canaux du côté qui peuvent se produire en raison de l’exécution spéculative d’une charge avance un magasin dépendant à la suite d’une mauvaise prédiction de l’accès mémoire.

Vous trouverez une introduction accessible à des vulnérabilités par canal latéral l’exécution spéculative dans la présentation intitulée [le cas de Spectre et Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) par une des équipes de recherche qui découvert ces problèmes.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>Quelles sont les vulnérabilités par canal de côté de l’exécution de spéculatif matériel ?

Unités centrales modernes offre un degré de performances en permettant l’utilisation de l’exécution spéculative et de désordre des instructions. Par exemple, cela s’effectue souvent en prédisant la cible des branches (conditionnels et indirects) qui permet à l’UC commencer spéculant l’exécution des instructions sur la cible de branche prédite, ce qui évite un blocage jusqu'à ce que la cible de branche réelle est résolu. Dans le cas où le processeur détecte ultérieurement qu’une mauvaise prédiction s’est produite, l’état de l’ordinateur qui a été calculé spéculant est perdue. Cela garantit qu’il n’y a aucun effet visible une architecture de la spéculation mal prédites retirée.

Pendant l’exécution spéculative n’affecte pas l’état visible de point de vue architectural, il peut laisse des traces qui sont restées dans un état non architecturales, telles que les caches différents qui sont utilisés par le processeur. Il s’agit de ces traces résiduelles de l’exécution spéculative qui peut donner lieu à des vulnérabilités par canal latéral. Pour mieux comprendre cela, prenons le fragment de code suivant qui fournit un exemple de CVE-2017-5753 (limites vérifier contournement) :

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

Dans cet exemple, `ReadByte` est fourni une mémoire tampon, une taille de mémoire tampon et un index dans le tampon. Le paramètre d’index, comme spécifié par `untrusted_index`, est fourni par un inférieur contexte privilégié, telles que d’un processus non administratifs. Si `untrusted_index` est inférieure à `buffer_size`, puis le caractère situé à cet index est en lecture à partir de `buffer` et utilisé pour l’index dans une région partagée de mémoire référencé par `shared_buffer`.

À partir d’un point de vue architectural, cette séquence de code est parfaitement sûr car il est garanti que `untrusted_index` sera toujours inférieur à `buffer_size`. Toutefois, en présence de l’exécution spéculative, il est possible que le processeur sera prédiction incorrecte la branche conditionnelle et exécuter le corps d’if instruction même lorsque `untrusted_index` est supérieur ou égal à `buffer_size`. Par conséquent, le processeur peut lire spéculant d’un octet ayant les limites de `buffer` (qui peut être un secret) et vous pouvez ensuite utiliser cette valeur d’octet pour calculer l’adresse d’un chargement ultérieur via `shared_buffer`.

Tandis que le processeur détecte finalement cette mauvaise prédiction, des effets secondaires qui sont restées peut rester dans le cache du processeur qui révèlent des informations sur la valeur d’octet qui a été lu en dehors des limites de `buffer`. Ces effets peuvent être détectées par un inférieur contexte privilégié en cours d’exécution sur le système en recherchant la vitesse à laquelle chaque cache dans ligne `shared_buffer` est accessible. Les étapes qui peuvent être prises pour effectuer cette opération sont :

1. **Appeler `ReadByte` plusieurs fois avec `untrusted_index` est inférieure à `buffer_size`** . Le contexte qui attaque peut entraîner le contexte de la victime appeler `ReadByte` (par exemple, via RPC) dont la prédiction de branche est formé à être pris ne pas en tant que `untrusted_index` est inférieure à `buffer_size`.

2. **Vider toutes les lignes de cache dans `shared_buffer`** . Le contexte qui attaque doit vider toutes les lignes de cache dans la région de mémoire référencé par partagée `shared_buffer`. Étant donné que la région de mémoire est partagée, cela est simple et qu’il peut être effectuée à l’aide des fonctions intrinsèques tels que `_mm_clflush`.

3. **Appeler `ReadByte` avec `untrusted_index` sont supérieures à `buffer_size`** . Le contexte qui attaque, le contexte de la victime appeler `ReadByte` telles qu’il prédit correctement que la branche ne sera pas prise. Cela provoque le processeur à exécuter spéculant le corps d’if bloc avec `untrusted_index` sont supérieures à `buffer_size`, ce qui conduit à une lecture hors limites de `buffer`. Par conséquent, `shared_buffer` est indexé à l’aide d’une valeur potentiellement confidentielles qui a été lu hors limites, ce qui entraîne la ligne de cache respectifs à charger par l’UC.

4. **Lire chaque ligne de cache dans `shared_buffer` pour voir ce qui est plus accéder rapidement aux**. Le contexte qui attaque peut lire chaque ligne de cache dans `shared_buffer` et détecter la ligne de cache qui charge beaucoup plus rapidement que les autres. Il s’agit de la ligne de cache est susceptible d’avoir été introduits par l’étape 3. Dans la mesure où il existe une relation de 1:1 entre la ligne de valeur et le cache des octets dans cet exemple, cela permet à un attaquant de déduire la valeur réelle de l’octet qui a été lu hors limites.

Les étapes ci-dessus fournissent un exemple d’utilisation d’une technique appelée vidage + recharger conjointement avec une instance de CVE-2017-5753 l’exploitation.

## <a name="what-software-scenarios-can-be-impacted"></a>Quels scénarios de logiciels peuvent être affectées ?

Développement de logiciels sécurisés à l’aide d’un processus comme le [Security Development Lifecycle](https://www.microsoft.com/sdl/) (SDL) requiert en général, les développeurs à identifier les limites de confiance qui existent dans leur application. Il existe une limite d’approbation dans les endroits où une application peut interagir avec les données fournies par un contexte de confiance moindre, comme un autre processus sur le système ou un processus de mode utilisateur non administrateur dans le cas d’un pilote de périphérique en mode noyau. La nouvelle classe de vulnérabilités impliquant des canaux du côté l’exécution spéculative s’applique à de nombreuses frontières d’approbation dans les modèles de sécurité logiciels existants qui isolent le code et les données sur un appareil.

Le tableau suivant fournit un résumé des modèles de sécurité logicielle où les développeurs devront peut-être être préoccupé par ces vulnérabilités qui se produisent :

|Limite d’approbation|Description|
|----------------|----------------|
|Limites de la machine virtuelle|Les applications qui isolent les charges de travail dans des machines virtuelles distinctes qui reçoivent des données non fiables à partir d’une autre machine virtuelle peuvent être menacée.|
|Limite du noyau|Un pilote de périphérique en mode noyau qui reçoit des données non fiables à partir d’un processus de mode utilisateur non-administrateur peut être menacée.|
|Limite de processus|Une application qui reçoit des données non fiables à partir d’un autre processus en cours d’exécution sur le système local, telles que via un appel de procédure distante (RPC), de mémoire partagée ou d’autres communications entre processus (IPC) mécanismes peuvent être menacée.|
|Limites de l’enclave|Une application qui s’exécute au sein d’une enclave sécurisée (par exemple, Intel SGX) qui reçoit des données non approuvées provenant en dehors de l’enclave soit compromise.|
|Barrière de langage|Une application qui interprète ou un juste à temps (JIT) compile et exécute le code non fiable écrit un langage de niveau supérieur peut être menacée.|

Applications qui ont surface d’attaque exposée à une de ces limites doivent vérifier le code sur la surface d’attaque pour identifier et réduire les occurrences possibles de vulnérabilités par canal latéral l’exécution spéculative d’approbation. Il convient de noter qu’exposés à des surfaces d’attaque à distance, tels que les protocoles réseau à distance, des limites d’approbation n’ont pas été démontrés à être exposé aux vulnérabilités par canal latéral l’exécution spéculative.

## <a name="potentially-vulnerable-coding-patterns"></a>Modèles de codage potentiellement vulnérables

Vulnérabilités par canal latéral l’exécution spéculative peuvent se produire en raison de plusieurs modèles de codage. Cette section décrit les modèles de codage potentiellement vulnérables et fournit des exemples pour chacune, mais il doit être reconnu que les variations sur ces thèmes peuvent exister. Par conséquent, les développeurs sont invités à prendre ces modèles comme exemples et non comme une liste exhaustive de tous les modèles de codage potentiellement vulnérables. Les mêmes classes de vulnérabilités de sécurité de mémoire qui peuvent exister dans le logiciel dès aujourd'hui peuvent exister le long spéculative et chemins d’accès de la sortie de commande d’exécution, y compris de manière non limitative, les dépassements de mémoire tampon, de tableau hors limites accès, utilisation de la mémoire non initialisée, type toute confusion et ainsi de suite. Les mêmes primitives utilisables par les pirates exploitent les vulnérabilités de sécurité de mémoire sur des tracés architecturales peuvent également s’appliquer aux chemins d’accès spéculatives.

En règle générale, mauvaise prédiction de l’exécution spéculative côté canaux associés à conditionnel branche peut se produire lorsqu’une expression conditionnelle opère sur les données qui peuvent être contrôlées ou influencées par un contexte de confiance moindre. Par exemple, cela peut inclure des expressions conditionnelles utilisées dans `if`, `for`, `while`, `switch`, ou d’instructions ternaires. Pour chacune de ces instructions, le compilateur peut générer une branche conditionnelle qui l’UC peut alors possible de prédire la cible de branche pour lors de l’exécution.

Pour chaque exemple, un commentaire de la phrase « Barrière de spéculation » est inséré dans lequel un développeur pourrait induire une barrière comme une atténuation. Ce sujet est abordé plus en détail dans la section sur les atténuations.

## <a name="speculative-out-of-bounds-load"></a>Charger spéculatif hors limites

Cette catégorie de modèles de codage implique une mauvaise prédiction de branchement conditionnel qui entraîne un spéculative hors limites accès à la mémoire.

### <a name="array-out-of-bounds-load-feeding-a-load"></a>Tableau hors limites charger une charge de l’alimentation

Ce modèle de codage est le modèle de codage vulnérable à l’origine décrit pour CVE-2017-5753 (limites vérifier contournement). La section de l’arrière-plan de cet article explique ce modèle en détail.

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

De même, un tableau hors limites charge peut se produire en conjonction avec une boucle qui dépasse son arrêt condition en raison d’une mauvaise prédiction. Dans cet exemple, la branche conditionnelle associé à la `x < buffer_size` expression peut de prédictions incorrectes et spéculant exécuter le corps de la `for` boucle lorsque `x` est supérieur ou égal à `buffer_size`, par conséquent, se traduisant par une spéculative charger hors limites.

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

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Tableau hors limites charger une branche indirecte de l’alimentation

Ce modèle de codage implique le cas où une mauvaise prédiction de branchement conditionnel peut entraîner un dépassement accès à un tableau de pointeurs de fonction qui entraîne ensuite une branche indirecte à la cible d’adresses qui a été lu hors limites. L’extrait de code suivant fournit un exemple illustrant cette approche.

Dans cet exemple, un identificateur de message non approuvé est fourni à DispatchMessage via le `untrusted_message_id` paramètre. Si `untrusted_message_id` est inférieure à `MAX_MESSAGE_ID`, il est utilisé pour indexer dans un tableau de pointeurs de fonction et créer une branche vers la cible de branche correspondante. Ce code est sécurisé de point de vue architectural, mais si l’UC prévisions incorrectes de la branche conditionnelle, cela peut entraîner `DispatchTable` indexées par `untrusted_message_id` lorsque sa valeur est supérieure ou égale à `MAX_MESSAGE_ID`, ce qui conduit à un accès hors limites. Cela peut entraîner l’exécution spéculative à partir d’une adresse de cible de branche est dérivée au-delà des limites du tableau, ce qui peut entraîner la divulgation d’informations en fonction du code qui est exécutée de manière spéculative.

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

Comme avec le cas d’un tableau hors limites charger une autre charge de l’alimentation, cette condition peut également survenir conjointement avec une boucle qui dépasse sa condition de fin en raison d’une mauvaise prédiction.

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>Tableau hors limites stocker une branche indirecte de l’alimentation

Bien que l’exemple précédent a montré comment un spéculative hors limites charge peut influencer une cible de branchement indirect, il est également possible pour un magasin hors limites pour modifier une cible de branchement indirecte, comme un pointeur de fonction ou une adresse de retour. Cela peut potentiellement entraîner l’exécution spéculative à partir d’une adresse spécifiée par l’attaquant.

Dans cet exemple, un index non approuvé est passé via le `untrusted_index` paramètre. Si `untrusted_index` est inférieur au nombre d’éléments de la `pointers` tableau (256 éléments), alors que la valeur de pointeur fourni dans `ptr` est écrit dans le `pointers` tableau. Ce code est sécurisé de point de vue architectural, mais si l’UC prévisions incorrectes de la branche conditionnelle, cela peut entraîner `ptr` spéculant écrite au delà des limites de la pile alloués `pointers` tableau. Cela peut entraîner une corruption de spéculative de l’adresse de retour pour `WriteSlot`. Si un attaquant peut contrôler la valeur de `ptr`, ils peuvent être en mesure de provoquer l’exécution spéculative à partir d’un texte arbitraire d’adresses lorsque `WriteSlot` retourne le long du tracé spéculatif.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

De même, si une variable locale de pointeur de fonction nommée `func` ont été allouées sur la pile, puis il est possible de modifier spéculant l’adresse qui `func` fait référence à des cas de la mauvaise prédiction de branchement conditionnel. Cela peut entraîner l’exécution spéculative à partir d’une adresse arbitraire lorsque le pointeur de fonction est appelé par le biais.

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

Il convient de noter que ces deux exemples impliquent la modification spéculative de pointeurs d’alloué par la pile de branche indirect. Il est possible que modification spéculative peut également se produire pour les variables globales, la mémoire alloués par tas et même la mémoire morte sur certains processeurs. Pour la mémoire allouée à la pile, le compilateur Visual C++ prend déjà les étapes pour le rendre plus difficile à modifier spéculant cibles alloué par la pile de branche indirecte, comme en réorganisant les variables locales telles que les mémoires tampons sont placées en position adjacentes à un cookie de sécurité en tant que dans le cadre de la [/GS](https://docs.microsoft.com/cpp/build/reference/gs-buffer-security-check) fonctionnalité de sécurité du compilateur.

## <a name="speculative-type-confusion"></a>Toute confusion type spéculative

Cette catégorie porte sur les modèles qui peuvent donner lieu à une confusion spéculative type de codage. Cela se produit lorsque la mémoire est accessible à l’aide d’un type incorrect sur un tracé non architecturales pendant l’exécution spéculative. Mauvaise prédiction de branchement conditionnel et magasin spéculative contournement susceptibles d’entraîner une confusion type spéculative.

Contournement de magasin spéculative, cela peut se produire dans les scénarios où un compilateur réutilise un emplacement de pile pour les variables de plusieurs types. Il s’agit, car le magasin architectural d’une variable de type `A` peut être contourné, autorisant ainsi la charge de type `A` spéculant exécuter avant que la variable est assignée. Si la variable précédemment stockée est d’un type différent, cela peut créer les conditions pour une confusion type spéculative.

Pour la mauvaise prédiction de branchement conditionnel, l’extrait de code suivant se servira pour décrire les différentes conditions toute confusion type spéculatives peut donner lieu à.

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

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Confusion type spéculative conduisant à une charge hors limites

Ce modèle de codage implique le cas où une confusion type spéculative peut entraîner un hors limites ou accès vous ne comprenez pas le type de champ où les flux de valeur chargée une adresse de chargement ultérieur. Cela est similaire au modèle de codage hors limites de tableau, mais il est identifié par le biais une alternative de séquence de codage comme indiqué ci-dessus. Dans cet exemple, un contexte qui attaque peut entraîner le contexte de la victime exécuter `ProcessType` plusieurs fois avec un objet de type `CType1` (`type` champ est égal à `Type1`). Cela aura l’effet de l’apprentissage de la branche conditionnelle pour la première `if` instruction pour ne prédire pas effectuée. Le contexte qui attaque peut provoquer ensuite le contexte de la victime exécuter `ProcessType` avec un objet de type `CType2`. Cela peut entraîner une confusion type spéculative si l’instruction conditionnelle de succursale pour la première `if` instruction prévisions incorrectes et exécute le corps de la `if` instruction, par conséquent, cast d’un objet de type `CType2` à `CType1`. Dans la mesure où `CType2` est inférieure à `CType1`, l’accès à la mémoire à `CType1::field2` résultat dans un spéculative se chargera hors limites de données qui peuvent être secrets. Cette valeur est ensuite utilisée dans une charge de `shared_buffer` qui peut créer des effets secondaires observables, comme avec le tableau hors limites exemple décrit précédemment.

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Confusion type spéculative conduisant à une branche indirecte

Ce modèle de codage implique le cas où une confusion type spéculatives peut entraîner une branche indirecte unsafe au cours de l’exécution spéculative. Dans cet exemple, un contexte qui attaque peut entraîner le contexte de la victime exécuter `ProcessType` plusieurs fois avec un objet de type `CType2` (`type` champ est égal à `Type2`). Cela aura l’effet de l’apprentissage de la branche conditionnelle pour la première `if` instruction à entreprendre et `else if` instruction à entreprendre ne pas. Le contexte qui attaque peut provoquer ensuite le contexte de la victime exécuter `ProcessType` avec un objet de type `CType1`. Cela peut entraîner une confusion type spéculative si l’instruction conditionnelle de succursale pour la première `if` instruction prédit prises et `else if` instruction ne prédit pas effectuée, exécutant ainsi le corps de la `else if` et cast d’un objet de type `CType1` à `CType2`. Dans la mesure où le `CType2::dispatch_routine` champ chevauche le `char` tableau `CType1::field1`, cela pourrait entraîner une branche indirecte spéculative vers une cible de branche involontaire. Si le contexte qui attaque peut contrôler les valeurs d’octets dans le `CType1::field1` tableau, ils peuvent être en mesure de contrôler l’adresse cible de branche.

## <a name="speculative-uninitialized-use"></a>Utilisation non initialisée spéculative

Cette catégorie de modèles de codage implique des scénarios où l’exécution spéculative peut accéder à la mémoire non initialisée et l’utiliser pour alimenter un chargement ultérieur ou une branche indirect. Pour ces modèles de codage être exploitable, un attaquant doit être en mesure de contrôler ou concrètement influencent le contenu de la mémoire qui est utilisé sans être initialisé par le contexte qu’il est utilisé dans.

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>Spéculative utilisation non initialisée, ce qui conduit à une charge hors limites

Une utilisation non initialisée spéculative susceptibles d’entraîner un hors limites de charge à l’aide d’une valeur contrôlé par l’attaquant. Dans l’exemple ci-dessous, la valeur de `index` est affecté `trusted_index` sur tous les chemins architecturales et `trusted_index` est supposé pour être inférieur ou égal à `buffer_size`. Toutefois, en fonction du code généré par le compilateur, il est possible qu’un contournement spéculative magasin peut se produire et qui permet de la charge à partir de `buffer[index]` et expressions dépendantes exécuté avant l’assignation à `index`. Si cela se produit, une valeur non initialisée pour `index` sera utilisé comme offset dans `buffer` qui permettrait à un attaquant de lire des informations sensibles hors limites et cela communiquent via un canal côté via le chargement dépendant de `shared_buffer` .

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

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>Utilisation de non initialisée spéculative conduisant à une branche indirecte

Une utilisation non initialisée spéculative susceptibles d’entraîner une branche indirecte où la cible de branche est contrôlée par une personne malveillante. Dans l’exemple ci-dessous, `routine` est affecté à une `DefaultMessageRoutine1` ou `DefaultMessageRoutine` selon la valeur de `mode`. Sur le chemin d’accès architectural, il en résulte `routine` toujours en cours d’initialisation avant la branche indirecte. Toutefois, en fonction du code généré par le compilateur, un contournement spéculative magasin peut se produire qui permet la branche indirecte via `routine` à exécuter avant l’assignation à spéculant `routine`. Si cela se produit, une personne malveillante peut être en mesure d’exécuter spéculant à partir d’une adresse arbitraire, en supposant que l’attaquant peut influencer ou contrôler la valeur non initialisée de `routine`.

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

Vulnérabilités par canal latéral l’exécution spéculative peuvent être atténuées en apportant des modifications au code source. Ces modifications peuvent impliquer d’atténuation des instances spécifiques d’une vulnérabilité, par exemple en ajoutant un *barrière de spéculation*, ou en apportant des modifications à la conception d’une application afin que des informations sensibles ne spéculative exécution.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Barrière de spéculation via une instrumentation manuelle

Un *barrière de spéculation* peut être insérée manuellement par un développeur pour empêcher l’exécution spéculative aboutir sur un tracé non architectural. Par exemple, un développeur peut insérer une barrière de spéculation avant un modèle de codage dangereux dans le corps d’un bloc conditionnel, soit au début du bloc (après la branche conditionnelle) ou avant le premier chargement est un critère important. Cela empêche une mauvaise prédiction de branchement conditionnel à partir de l’exécution du code dangereux sur un chemin d’accès non architecturale en sérialisant l’exécution. La séquence de barrière de spéculation diffère par architecture matérielle comme décrit dans le tableau suivant :

|Architecture|Barrière de spéculation intrinsèque pour CVE-2017-5753|Barrière de spéculation intrinsèque pour CVE-2018-3639|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence()|_mm_lfence()|
|ARM|actuellement non disponible|__dsb(0)|
|ARM64|actuellement non disponible|__dsb(0)|

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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Barrière de spéculation via l’instrumentation de compilateur-heure

Le compilateur Visual C++ dans Visual Studio 2017 (à partir de la version 15.5.5) prend en charge la `/Qspectre` commutateur qui insère automatiquement une barrière de spéculation pour un ensemble limité de modèles de codage potentiellement vulnérables liés à CVE-2017-5753. La documentation relative à la [/qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre) indicateur fournit plus d’informations sur l’utilisation et ses effets. Il est important de noter que cet indicateur ne couvre pas tous les modèles de codage potentiellement vulnérables et par conséquent les développeurs ne doivent pas y recourir comme une atténuation complète pour cette classe de vulnérabilités.

### <a name="masking-array-indices"></a>Masquage des indices de tableau

Dans les cas où un spéculative hors limites de charge peut se produire, l’index de tableau peut fortement limité sur le chemin architectural et non architecturales par ajout d’une logique pour liés explicitement l’index de tableau. Par exemple, si un tableau peut être affecté à une taille qui est alignée sur une puissance de deux, puis un masque simple peut être introduit. Ceci est illustré dans l’exemple ci-dessous, où il est supposé que `buffer_size` est alignée à une puissance de deux. Cela garantit que `untrusted_index` est toujours inférieure à `buffer_size`, même en cas d’une mauvaise prédiction de branchement conditionnel et `untrusted_index` a été passé avec une valeur supérieure ou égale à `buffer_size`.

Il convient de noter que le masquage de l’index effectué ici peut être soumis à contournement store spéculatives selon le code généré par le compilateur.

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

### <a name="removing-sensitive-information-from-memory"></a>Suppression des informations sensibles de la mémoire

Une autre technique qui peut être utilisée pour atténuer les vulnérabilités par canal latéral l’exécution spéculative consiste à supprimer les informations sensibles de la mémoire. Les développeurs de logiciels peuvent rechercher les opportunités de refactoriser leur application, telles que des informations sensibles ne sont pas accessibles pendant l’exécution spéculative. Pour cela, en refactorisant la conception d’une application pour isoler des informations sensibles dans des processus distincts. Par exemple, une application de navigateur web peut tenter d’isoler les données associées à chaque origine web dans des processus distincts, empêchant ainsi un processus d’être en mesure d’accéder aux données de cross-origine via l’exécution spéculative.

## <a name="see-also"></a>Voir aussi

[Conseils pour atténuer les vulnérabilités par canal latéral l’exécution spéculative](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[Atténuer les vulnérabilités de matériel de l’exécution spéculative côté canal](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
