---
title: Conversions de type définies par l'utilisateur (C++)
ms.date: 11/04/2016
f1_keywords:
- explicit_cpp
helpviewer_keywords:
- constructors [C++], and constants
- conversion functions [C++]
- explicit keyword [C++]
- type conversion
- constructors [C++], drawbacks
- conversion constructors
- type conversion [C++], explicit conversion
- coercion [C++]
- conversions [C++], explicit
- objects [C++], converting
- conversion functions [C++], rules for declaring
- declaring functions [C++], conversion functions
- functions [C++], conversion
- converting objects
- constructors [C++], conversion
- conversions [C++], by constructors
- data type conversion [C++], explicit
ms.assetid: d40e4310-a190-4e95-a34c-22c5c20aa0b9
ms.openlocfilehash: 2af30ad3d1244146f32bf2402ed7eccdc4785c1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459889"
---
# <a name="user-defined-type-conversions-c"></a>Conversions de type définies par l'utilisateur (C++)

Un *conversion* génère une nouvelle valeur d’un type à partir d’une valeur d’un type différent. *Conversions standard* sont intégrées dans le langage C++ et la prise en charge ses types intégrés et vous pouvez créer *conversions définies par l’utilisateur* pour effectuer des conversions vers, depuis ou entre les types définis par l’utilisateur.

Les conversions standard effectuent des conversions entre des types intégrés, entre des pointeurs ou références vers des types apparentés par héritage, vers et à partir de pointeurs void, et vers le pointeur null. Pour plus d’informations, consultez [Conversions Standard](../cpp/standard-conversions.md). Les conversions définies par l'utilisateur effectuent des conversions entre des types définis par l'utilisateur ou entre des types définis par l'utilisateur et des types intégrés. Vous pouvez les implémenter en tant que [constructeurs de Conversion](#ConvCTOR) ou en tant que [fonctions de Conversion](#ConvFunc).

Les conversions peuvent être explicites (quand le programmeur appelle un type pour qu'il soit converti en un autre type, comme dans une diffusion ou une initialisation directe) ou implicites (quand le langage ou le programme appelle un autre type que celui qui a été donné par le programmeur).

Les conversions implicites sont tentées dans les conditions suivantes :

- un argument fourni à une fonction n'est pas du même type que le paramètre correspondant ;

- la valeur retournée d'une fonction n'est pas du même type que le type de retour de la fonction ;

- une expression d'initialiseur n'est pas du même type que l'objet qu'elle initialise ;

- une expression qui contrôle une instruction conditionnelle, une construction de boucles ou un commutateur n'est pas du type requis pour exercer ce contrôle.

- un opérande fourni à un opérateur n'est pas du même type que le paramètre d'opérande correspondant. Pour les opérateurs intégrés, les deux opérandes doivent être du même type et sont convertis en un type commun qui représente les deux. Pour plus d’informations, consultez [Conversions Standard](standard-conversions.md). Pour les opérateurs définis par l’utilisateur, chaque opérande doit être du même type que le paramètre d’opérande correspondant.

Quand une conversion standard ne peut pas terminer une conversion implicite, le compilateur peut utiliser une conversion définie par l'utilisateur, suivie éventuellement d'une autre conversion standard, pour la terminer.

Quand plusieurs conversions définies par l'utilisateur effectuant la même conversion sont disponibles sur un site de conversion, la conversion est dite ambiguë. Ces ambiguïtés sont une erreur, car le compilateur ne peut pas déterminer quelle conversion choisir parmi les conversions disponibles. Toutefois, ce n'est pas une erreur de définir plusieurs façons d'effectuer la même conversion, car l'ensemble des conversions disponibles peut être différent selon l'emplacement où elles se trouvent dans le code source (par exemple, en fonction des fichiers d'en-tête inclus dans un fichier source). Si une seule conversion est disponible sur le site de conversion, il n'y a pas d'ambiguïté. Il existe plusieurs raisons aux conversions ambiguës, mais les plus courantes sont les suivantes :

- Héritage multiple. La conversion est définie dans plusieurs classes de base.

- Appel de fonction ambigu. La conversion est définie en tant que constructeur de conversion du type cible et en tant que fonction de conversion du type source. Pour plus d’informations, consultez [fonctions de Conversion](#ConvFunc).

Vous pouvez généralement résoudre une ambiguïté en qualifiant le nom du type impliqué de manière plus complète ou en effectuant une diffusion explicite pour clarifier votre intention.

Les constructeurs de conversion et les fonctions de conversion sont régis par des règles de contrôle d'accès par membre, mais l'accessibilité des conversions n'est possible que si et quand une conversion n'est pas considérée comme ambiguë. Cela signifie qu'une conversion peut être ambiguë même si le niveau d'accès d'une conversion concurrente l'empêche d'être utilisée. Pour plus d’informations sur l’accessibilité des membres, consultez [contrôle d’accès de membre](../cpp/member-access-control-cpp.md).

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Le mots clé explicite et les problèmes liés à la conversion implicite

Par défaut, quand vous créez une conversion définie par l'utilisateur, le compilateur peut l'utiliser pour effectuer des conversions implicites. Parfois, c'est ce que vous voulez, mais parfois, les règles simples qui guident le compilateur dans la création de conversions implicites peut l'amener à accepter du code qu'il ne devrait pas.

Un exemple bien connu de conversion implicite qui peut entraîner des problèmes est la conversion en **bool**. Il existe diverses raisons, vous souhaiterez peut-être créer un type de classe qui peut être utilisé dans un contexte Boolean — par exemple, par conséquent, qu’elle peut être utilisée au contrôle un **si** boucle ou instruction, mais lorsque le compilateur effectue une conversion définie par l’utilisateur à un type intégré, le compilateur est autorisé à appliquer une conversion standard supplémentaire par la suite. L’objectif de cette conversion standard supplémentaire est d’autoriser des actions comme la promotion de **court** à **int**, mais elle ouvre également la porte pour les conversions moins évidentes, par exemple, à partir de  **bool** à **int**, ce qui permet à votre type de classe à utiliser dans des contextes d’entiers que vous aviez jamais l’intention. Ce problème particulier est connu comme le *problème Safe Bool*. Ce type de problème est là le **explicite** mot clé peut aider.

Le **explicite** mot clé indique au compilateur que la conversion spécifiée ne peut pas être utilisée pour effectuer des conversions implicites. Si vous vouliez la commodité syntaxique des conversions implicites avant le **explicite** mot clé a été introduit, vous deviez utiliser moins pratiques, soit accepter les conséquences imprévues parfois créée par la conversion implicite fonctions de conversion nommée comme une solution de contournement. Maintenant, à l’aide de la **explicite** mot clé, vous pouvez créer des conversions pratiques qui peut uniquement être utilisé pour effectuer des conversions explicites ou une initialisation directe, et qui n’entraîneront pas le type de problème illustré par le problème Safe Bool.

Le **explicite** mot clé peut être appliqué aux constructeurs de conversion depuis C ++ 98 et aux fonctions de conversion depuis C ++ 11. Les sections suivantes contiennent plus d’informations sur l’utilisation de la **explicite** mot clé.

## <a name="ConvCTOR"></a> Constructeurs de conversion

Les constructeurs de conversion définissent les conversions de types définis par l'utilisateur ou intégrés en type défini par l'utilisateur. L’exemple suivant illustre un constructeur de conversion qui convertit le type intégré **double** à un type défini par l’utilisateur `Money`.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };

    display_balance(payable);
    display_balance(49.95);
    display_balance(9.99f);

    return 0;
}
```

Notez que le premier appel de la fonction `display_balance`, qui prend un argument de type `Money`, ne requiert aucune conversion, car le type de son argument est correct. Toutefois, sur le deuxième appel à `display_balance`, une conversion est nécessaire, car le type de l’argument, un **double** avec la valeur `49.95`, n’est pas ce que la fonction attend. La fonction ne peut pas utiliser cette valeur directement, mais parce qu’il existe une conversion à partir du type de l’argument —**double**— au type du paramètre correspondant,`Money`— une valeur temporaire de type `Money` est construit à partir de l’argument et permet de terminer l’appel de fonction. Dans le troisième appel `display_balance`, notez que l’argument n’est pas un **double**, mais est plutôt un **float** avec la valeur `9.99`— et encore l’appel de fonction peut toujours être effectué, car le compilateur peut effectuer une conversion standard — dans ce cas, à partir de **float** à **double**, puis d’effectuer la conversion définie par l’utilisateur à partir de **double** à `Money` pour terminer la conversion nécessaire.

### <a name="declaring-conversion-constructors"></a>Déclaration des constructeurs de conversion

Les règles suivantes s'appliquent à la déclaration d'un constructeur de conversion :

- Le type cible de la conversion est le type défini par l'utilisateur en cours de construction.

- Les constructeurs de conversion prennent généralement un seul argument, qui est de type source. Toutefois, un constructeur de conversion peut spécifier d'autres paramètres si chaque paramètre supplémentaire a une valeur par défaut. Le type source reste le type du premier paramètre.

- Les constructeurs de conversion, comme tous les constructeurs, ne spécifient pas de type de retour. La spécification d'un type de retour dans la déclaration constitue une erreur.

- Les constructeurs de conversion peuvent être explicites.

### <a name="explicit-conversion-constructors"></a>Constructeurs de conversion explicites

En déclarant un constructeur de conversion doit être **explicite**, il peut uniquement être utilisé pour effectuer une initialisation directe d’un objet ou pour effectuer un cast explicite. Cela empêche les fonctions acceptant un argument du type de la classe d’accepter également de manière implicite des arguments du type source du constructeur de conversion, et empêche le type de la classe d’être initialisé par copie d’une valeur du type source. L'exemple suivant décrit comment définir un constructeur de conversion explicite et son impact sur le code formé correctement.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    explicit Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };        // Legal: direct initialization is explicit.

    display_balance(payable);      // Legal: no conversion required
    display_balance(49.95);        // Error: no suitable conversion exists to convert from double to Money.
    display_balance((Money)9.99f); // Legal: explicit cast to Money

    return 0;
}
```

Dans cet exemple, notez que vous pouvez encore utiliser le constructeur de conversion explicite pour effectuer une initialisation directe de `payable`. Si au lieu de cela vous devez initialiser par copie `Money payable = 79.99;`, cela constituerait une erreur. Le premier appel de `display_balance` n'est pas affecté, car l'argument est de type correct. Le deuxième appel de `display_balance` constitue une erreur, car le constructeur de conversion ne peut pas être utilisé pour effectuer des conversions implicites. Le troisième appel `display_balance` est autorisé en raison de la conversion explicite vers `Money`, mais notez que le compilateur a encore aidé à terminer le transtypage en insérant un transtypage implicite de **float** à **double**.

Même si vous pouvez être tenté par la commodité de l'autorisation des conversions implicites, celle-ci peut introduire des bogues difficiles à trouver. De manière générale, il vaut mieux que tous les constructeurs de conversion soient explicites, sauf quand vous êtes sûr que vous voulez qu'une conversion spécifique se produise de manière implicite.

##  <a name="ConvFunc"></a> Fonctions de conversion

Les fonctions de conversion définissent des conversions d'un type défini par l'utilisateur en d'autres types. Ces fonctions sont parfois qualifiées d'« opérateurs de transtypage », car elles sont appelées, en même temps que les constructeurs de conversion, quand une valeur est transtypée vers un type différent. L’exemple suivant montre une fonction de conversion qui convertit le type défini par l’utilisateur, `Money`, pour un type intégré, **double**:

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance << std::endl;
}
```

Notez que la variable membre `amount` devient privé et qu’une conversion publique fonctionne en type **double** est introduite uniquement pour retourner la valeur de `amount`. Dans la fonction `display_balance`, une conversion implicite se produit quand la valeur de `balance` est diffusée sur la sortie standard à l'aide de l'opérateur d'insertion de flux `<<`. Car aucun opérateur d’insertion de flux n’est défini pour le type défini par l’utilisateur `Money`, mais il en existe un pour le type intégré **double**, le compilateur peut utiliser la fonction de conversion à partir de `Money` à **double** pour satisfaire l’opérateur d’insertion de flux.

Les fonctions de conversion sont héritées dans les classes dérivées. Les fonctions de conversion d'une classe dérivée ne peuvent remplacer une fonction de conversion héritée que lorsqu'elles convertissent vers le même type exactement. Par exemple, une fonction de conversion définie par l’utilisateur de la classe dérivée **opérateur int** ne remplace pas, ni influence, une fonction de conversion définie par l’utilisateur de la classe de base **opérateur short**, même Bien que les conversions standard définissent une relation de conversion entre **int** et **court**.

### <a name="declaring-conversion-functions"></a>Déclaration des fonctions de conversion

Les règles suivantes s'appliquent à la déclaration d'une fonction de conversion :

- Le type cible de la conversion doit être déclaré avant la déclaration de la fonction de conversion. Les classes, structures, énumérations et typedefs ne peuvent pas être déclarés dans la déclaration de la fonction de conversion.

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- Les fonctions de conversion ne prennent pas d'arguments. La spécification d'un paramètre dans la déclaration constitue une erreur.

- Les fonctions de conversion ont un type de retour spécifié par le nom de la fonction de conversion, qui est également le nom du type cible de la conversion. La spécification d'un type de retour dans la déclaration constitue une erreur.

- Les fonctions de conversion peuvent être virtuelles.

- Les fonctions de conversion peuvent être explicites.

### <a name="explicit-conversion-functions"></a>Fonctions de conversion explicites

Quand une fonction de conversion est déclarée comme explicite, elle ne peut être utilisée que pour effectuer un transtypage explicite. Cela empêche les fonctions acceptant un argument du type cible de la fonction de conversion d'accepter également de manière implicite des arguments du type de la classe, et empêche les instances du type cible d'être initialisées par copie d'une valeur du type de la classe. L'exemple suivant décrit comment définir une fonction de conversion explicite et son impact sur le code formé correctement.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    explicit operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << (double)balance << std::endl;
}
```

Ici, la fonction de conversion **double (opérateur)** explicitement et une conversion explicite en type **double** a été introduite dans la fonction `display_balance` pour effectuer la conversion. Si ce transtypage est omis, le compilateur est incapable de rechercher un opérateur d'insertion de flux `<<` convenable pour le type `Money` et une erreur se produit.