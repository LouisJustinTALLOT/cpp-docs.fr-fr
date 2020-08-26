---
title: Avertissements du compilateur désactivés par défaut
ms.date: 08/29/2019
helpviewer_keywords:
- warnings, compiler
- cl.exe compiler, setting options
ms.assetid: 69809cfb-a38a-4035-b154-283a61938df8
ms.openlocfilehash: 3727777c6abd3ae5ba19f147e2b6fbe559251813
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836607"
---
# <a name="compiler-warnings-that-are-off-by-default"></a>Avertissements du compilateur désactivés par défaut

Le compilateur prend en charge les avertissements qui sont désactivés par défaut, car la plupart des développeurs ne les trouvent pas utiles. Dans certains cas, ils signalent un choix stylistique ou des idiomes courants dans du code plus ancien. D’autres avertissements concernent l’utilisation d’une extension Microsoft pour le langage. Certains avertissements indiquent une zone dans laquelle les programmeurs font souvent des hypothèses incorrectes, ce qui peut entraîner un comportement inattendu ou non défini. Si tous ces avertissements sont activés, certains d’entre eux peuvent apparaître plusieurs fois dans les en-têtes de bibliothèque. Les bibliothèques Runtime C et les bibliothèques C++ standard sont destinées à émettre aucun avertissement uniquement au niveau d’avertissement [/W4](../build/reference/compiler-option-warning-level.md).

## <a name="enable-warnings-that-are-off-by-default"></a>Activer les avertissements qui sont désactivés par défaut

Vous pouvez activer les avertissements qui sont normalement désactivés par défaut en utilisant l’une des options suivantes :

- **avertissement #pragma (valeur par défaut :** *warning_number* **)**

   L’avertissement spécifié (*warning_number*) est activé à son niveau par défaut. La documentation de l'avertissement contient le niveau par défaut de l'avertissement.

- **Avertissement #pragma (** *warning_level* **:** *warning_number* **)**

   L’avertissement spécifié (*warning_number*) est activé au niveau spécifié (*warning_level*).

- [/Wall](../build/reference/compiler-option-warning-level.md)

   `/Wall` active tous les avertissements qui sont désactivés par défaut. Si vous utilisez cette option, vous pouvez désactiver des avertissements individuels à l’aide de l’option [/WD](../build/reference/compiler-option-warning-level.md) .

- [/w*Lnnnn*](../build/reference/compiler-option-warning-level.md)

   Cette option active l’avertissement *nnnn* au niveau *L*.

## <a name="warnings-that-are-off-by-default"></a>Avertissements désactivés par défaut

Les avertissements suivants sont désactivés par défaut dans Visual Studio 2015 et versions ultérieures :

|Avertissement|Message|
|-|-|
|[C4061](../error-messages/compiler-warnings/compiler-warning-level-4-c4061.md) (niveau 4)|l’énumérateur'*identificateur*'dans un switch de l’enum'*énumération*'n’est pas géré explicitement par une étiquette case|
|[C4062](../error-messages/compiler-warnings/compiler-warning-level-4-c4062.md) (niveau 4)|l’énumérateur'*identificateur*'dans un switch de l’enum'*énumération*'n’est pas géré|
| [C4165](../error-messages/compiler-warnings/compiler-warning-level-1-c4165.md) (niveau 1) | 'HRESULT’est en cours de conversion en’bool'; êtes-vous sûr de vouloir cela ? |
| [C4191](../error-messages/compiler-warnings/compiler-warning-level-3-c4191.md) (niveau 3)|'*Operator*' : conversion risquée de'*type_of_expression*'en'*type_required*'|
|[C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) (niveau 4)|'*identificateur*' : conversion de'*type1*'en'*type2*', perte possible de données|
|[C4254](../error-messages/compiler-warnings/compiler-warning-level-4-c4254.md) (niveau 4)|'*opérateur*' : conversion de'*type1*'en'*type2*', perte possible de données|
|[C4255](../error-messages/compiler-warnings/compiler-warning-level-4-c4255.md) (niveau 4)|'*fonction*' : aucun prototype de fonction fourni : conversion de' () 'en' (void) '|
|[C4263](../error-messages/compiler-warnings/compiler-warning-level-4-c4263.md) (niveau 4)|'*fonction*' : la fonction membre ne se substitue à aucune fonction membre virtuelle de classe de base|
|[C4264](../error-messages/compiler-warnings/compiler-warning-level-1-c4264.md) (niveau 1)|'*virtual_function*' : aucune substitution disponible pour la fonction membre virtuelle à partir de la classe de base'*classe*'; la fonction est masquée|
|[C4265](../error-messages/compiler-warnings/compiler-warning-level-3-c4265.md) (niveau 3)|'*classe*' : la classe a des fonctions virtuelles, mais le destructeur n’est pas virtuel|
|[C4266](../error-messages/compiler-warnings/compiler-warning-level-4-c4266.md) (niveau 4)|'*fonction*' : aucune substitution disponible pour la fonction membre virtuelle à partir de'*type*'de base ; la fonction est masquée|
|[C4287](../error-messages/compiler-warnings/compiler-warning-level-3-c4287.md) (niveau 3)|'*opérateur*' : incompatibilité constante non signée/négative|
|[C4289](../error-messages/compiler-warnings/compiler-warning-level-4-c4289.md) (niveau 4)|extension non standard utilisée : '*var*' : la variable de contrôle de boucle déclarée dans la boucle for est utilisée en dehors de la portée de la boucle|
|[C4296](../error-messages/compiler-warnings/compiler-warning-level-4-c4296.md) (niveau 4)|'*opérateur*' : l’expression est toujours false|
|[C4339](../error-messages/compiler-warnings/compiler-warning-level-4-c4339.md) (niveau 4)|'*type*' : utilisation d’un type non défini détecté dans les métadonnées CLR-l’utilisation de ce type peut provoquer une exception Runtime|
|[C4342](../error-messages/compiler-warnings/compiler-warning-level-1-c4342.md) (niveau 1)|changement de comportement : '*Function*'appelé, mais un opérateur de membre a été appelé dans les versions précédentes|
|[C4350](../error-messages/compiler-warnings/compiler-warning-level-1-c4350.md) (niveau 1)|changement de comportement : '*membre1*'appelé à la place de'*membre2*'|
|[C4355](../error-messages/compiler-warnings/compiler-warning-c4355.md)|'this' : utilisé dans la liste des initialiseurs membre de base|
|[C4365](../error-messages/compiler-warnings/compiler-warning-level-4-c4365.md) (niveau 4)|'*action*' : conversion de'*TYPE_1*'en'*type_2*', incompatibilité signed/unsigned|
|C4370 (niveau 3)|la disposition de classe a été modifiée à partir d'une version précédente du compilateur en raison d'une meilleure compression|
|[C4371](../error-messages/compiler-warnings/c4371.md) (niveau 3)|'*className*' : la disposition de la classe peut avoir été modifiée à partir d’une version précédente du compilateur en raison d’une meilleure compression du membre'*member*'|
|C4388 (niveau 4)|incompatibilité signed/unsigned|
|[C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md) (niveau 2)|'*fonction*' : la signature de fonction contient le type'*type*'; Les objets C++ ne sont pas sûrs à passer entre le code pur et le code mixte ou natif|
|C4426 (niveau 1)|indicateurs d’optimisation modifiés après l’ajout de l’en-tête, peut être dû à #pragma optimize () <sup>14,1</sup>|
|[C4435](../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md) (niveau 4)|'*classe1*' : la disposition des objets sous/VD2 sera modifiée en raison de la base virtuelle'*Class2*'|
|[C4437](../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md) (niveau 4)|l’dynamic_cast de la base virtuelle «*classe1*» à «*Class2*» peut échouer dans certains contextes|
|C4444 (niveau 3)|'__unaligned' de niveau supérieur n'est pas implémenté dans ce contexte|
|[C4464](../error-messages/compiler-warnings/c4464.md) (niveau 4)|le chemin d’accès include relatif contient'.. '|
|[C4471](../error-messages/compiler-warnings/compiler-warning-level-4-c4471.md) (niveau 4)|une déclaration anticipée d’une énumération non délimitée doit avoir un type sous-jacent (int supposé) <sup>Perm</sup>|
|C4472 (niveau 1)|'*identifier*'est un enum natif : ajoutez un spécificateur d’accès (Private/Public) pour déclarer une énumération managée|
|[C4514](../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md) (niveau 4)|'*fonction*' : la fonction inline non référencée a été supprimée|
|[C4536](../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md) (niveau 4)|'nom de type' : le nom de type dépasse la limite de métadonnées de'*Limit*'caractères|
|[C4545](../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md) (niveau 1)|l’expression avant la virgule correspond à une fonction qui n’a pas de liste d’arguments|
|[C4546](../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md) (niveau 1)|l’appel de fonction avant la virgule n’a pas de liste d’arguments|
|[C4547](../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md) (niveau 1)|'*opérateur*' : l’opérateur avant la virgule n’a aucun effet ; opérateur avec effet secondaire ATTENDU|
|[C4548](../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md) (niveau 1)|l'expression avant la virgule n'a pas d'effet ; expression avec effet secondaire attendu|
|[C4549](../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md) (niveau 1)|'*operator1*' : l’opérateur avant la virgule n’a aucun effet ; souhaitiez-vous'*operator2*' ?|
|[C4555](../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md) (niveau 1)|l'expression n'a pas d'effet ; attendue expression avec effets secondaires|
|[C4557](../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md) (niveau 3)|' __assume’contient l’effet *'effect'*|
|[C4571](../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md) (niveau 4)|informations : la sémantique catch (...) a changé depuis Visual C++ 7,1 ; les exceptions structurées (SEH) ne sont plus interceptées|
|C4574 (niveau 4)|'*identifier*'est défini comme étant' 0 ' : vouliez-vous utiliser' #if *identificateur*' ?|
|C4577 (niveau 1)|'noexcept’utilisé sans le mode de gestion des exceptions spécifié ; l’arrêt en cas d’exception n’est pas garanti. Spécifier/EHsc|
|C4582 (niveau 4)|'*type*' : le constructeur n’est pas appelé implicitement|
|C4583 (niveau 4)|'*type*' : le destructeur n’est pas appelé implicitement|
|C4587 (niveau 1)|'*anonymous_structure*' : changement de comportement : le constructeur n’est plus appelé de manière implicite|
|C4588 (niveau 1)|'*anonymous_structure*' : changement de comportement : le destructeur n’est plus appelé de manière implicite|
|[C4596](../error-messages/compiler-warnings/c4596.md) (niveau 4)|'*identificateur*' : nom qualifié non conforme dans la déclaration de membre <sup>14,3</sup> <sup>Perm</sup>|
|C4598 (niveau 1 et niveau 3)|*en-* tête « #include » «» : le numéro d’en- *tête* du numéro d’en-tête dans l’en-tête précompilé ne correspond pas à la compilation actuelle à cette position <sup>14,3</sup>|
|C4599 (niveau 3)|'*option* *path*' : le numéro d’argument de ligne de commande ne correspond pas au *nombre* d’en-tête précompilé <sup>14,3</sup>|
|C4605 (niveau 1)|'/D*macro*'spécifié sur la ligne de commande actuelle, mais n’a pas été spécifié quand l’en-tête précompilé a été généré|
|[C4608](../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md) (niveau 3)|'*union_member*'a déjà été initialisé par un autre membre Union dans la liste d’initialiseurs, '*union_member*' <sup>Perm</sup>|
|[C4619](../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md) (niveau 3)|Avertissement de #pragma : il n’y a aucun numéro d’avertissement'*numéro*'|
|[C4623](../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md) (niveau 4)|'classe dérivée' : le constructeur par défaut n'a pas pu être généré parce que le constructeur par défaut de la classe de base est inaccessible|
|[C4625](../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md) (niveau 4)|'classe dérivée' : le constructeur de copie n'a pas pu être généré parce qu'un constructeur de copie de la classe de base est inaccessible|
|[C4626](../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md) (niveau 4)|'classe dérivée' : l'opérateur d'assignation n'a pas pu être généré parce qu'un opérateur d'assignation de la classe de base est inaccessible|
|[C4628](../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md) (niveau 1)|digrammes non pris en charge avec -Ze. Séquence de caractères'*digramme*'non interprétée comme jeton de remplacement pour'*char*'|
|[C4640](../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md) (niveau 3)|'*instance*' : la construction d’un objet static local n’est pas thread-safe|
| C4643 (niveau 4) | La déclaration anticipée'*identifier*'dans l’espace de noms std n’est pas autorisée par la norme C++. <sup>15.8</sup> |
|C4647 (niveau 3)|changement de comportement : __is_pod (*type*) a une valeur différente dans les versions précédentes|
|C4654 (niveau 4)|Le code placé avant l’inclusion de la ligne d’en-tête précompilé sera ignoré. Ajoutez du code à l’en-tête précompilé. <sup>14,1</sup>|
|[C4668](../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md) (niveau 4)|'*symbol*'n’est pas défini en tant que macro de préprocesseur, remplaçant par' 0 'pour'*directives*'|
|[C4682](../error-messages/compiler-warnings/compiler-warning-level-4-c4682.md) (niveau 4)|'*symbol*' : aucun attribut de paramètre directionnel spécifié, [in] par défaut|
|[C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md) (niveau 3)|'*type défini par l’utilisateur*' : changement de comportement possible, modification de la Convention d’appel de retour UDT|
|[C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md) (niveau 1)|'*fonction*' : la signature d’un membre non privé contient un type natif privé d’assembly'*NATIVE_TYPE*'|
|[C4710](../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md) (niveau 4)|'*fonction*' : fonction non inline|
|[C4738](../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md) (niveau 3)|stockage de résultat flottant 32 bits en mémoire, perte possible de performances|
|[C4746](../error-messages/compiler-warnings/compiler-warning-c4746.md)|l’accès volatile de'*expression*'est soumis à/volatile : \<iso&#124;ms> Setting ; envisagez d’utiliser __iso_volatile_load fonctions intrinsèques/Store|
|C4749 (niveau 4)|pris en charge de manière conditionnelle : OffsetOf appliqué au type de disposition non standard'*type*'|
|C4767 (niveau 4)|le nom de section'*symbol*'comporte plus de 8 caractères et sera tronqué par l’éditeur de liens|
|C4768 (niveau 3)|__declspec attributs avant la spécification de la liaison sont ignorés|
|C4774 (niveau 4)|'*String*' : la chaîne de format attendue dans l’argument *Number* n’est pas un littéral de chaîne|
|C4777 (niveau 4)|'*fonction*' : la chaîne de mise en forme'*chaîne*'requiert un argument de type'*type1*', mais le *numéro* d’argument variadiques a le type'*type2*'|
|C4786 (niveau 3)|'*symbol*' : le nom de l’objet a été tronqué en'*Number*'caractères dans les informations de débogage|
| [C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) (niveau 4) | Conversion implicite de'*type*'en bool. Perte d’informations possible <sup>16,0</sup> |
|[C4820](../error-messages/compiler-warnings/compiler-warning-level-4-c4820.md) (niveau 4)|le remplissage des octets'*bytes*'a été ajouté après la construction'*Member_Name*'|
| [C4822](../error-messages/compiler-warnings/compiler-warning-level-1-c4822.md) (niveau 1) | '*membre*' : la fonction membre de classe locale n’a pas de corps |
|C4826 (niveau 2)|La conversion de'*type1*'en'*type2*'est un signe étendu. Cela peut entraîner un comportement inattendu du Runtime.|
|C4837 (niveau 4)|trigraphe détecté : ' ?? *caractère*'remplacé par'*caractère*'|
|C4841 (niveau 4)|extension non standard utilisée : désignateur de membre composé utilisé dans OffsetOf|
|C4842 (niveau 4)|le résultat de’OffsetOf’appliqué à un type utilisant plusieurs héritages n’est pas nécessairement cohérent entre les versions du compilateur|
|[C4868](../error-messages/compiler-warnings/compiler-warning-c4868.md) (niveau 4)|le compilateur'_file_(*line_number*) 'ne peut pas appliquer l’ordre d’évaluation de gauche à droite dans la liste d’initialisation entre accolades|
|[C4905](../error-messages/compiler-warnings/compiler-warning-level-1-c4905.md) (niveau 1)|cast de littéral de chaîne étendu en 'LPSTR'|
|[C4906](../error-messages/compiler-warnings/compiler-warning-level-1-c4906.md) (niveau 1)|cast de littéral de chaîne en 'LPWSTR'|
|[C4917](../error-messages/compiler-warnings/compiler-warning-level-1-c4917.md) (niveau 1)|'*déclarateur*' : un GUID ne peut être associé qu’à une classe, une interface ou un espace de noms|
|[C4928](../error-messages/compiler-warnings/compiler-warning-level-1-c4928.md) (niveau 1)|initialisation de copie non conforme ; plusieurs conversions définies par l'utilisateur ont été appliquées implicitement|
|[C4931](../error-messages/compiler-warnings/compiler-warning-level-4-c4931.md) (niveau 4)|bibliothèque de types présumée construite pour des pointeurs 'nombre' bits|
|[C4946](../error-messages/compiler-warnings/compiler-warning-level-1-c4946.md) (niveau 1)|reinterpret_cast utilisées entre des classes connexes : '*Class1*'et'*Class2*'|
|C4962|'*fonction*' : les optimisations guidées par profil sont désactivées, car les optimisations ont provoqué l’incohérence des données de profil|
|[C4986](../error-messages/compiler-warnings/compiler-warning-c4986.md) (niveau 4)|'*symbol*' : la spécification d’exception ne correspond pas à la déclaration précédente|
|C4987 (niveau 4)|extension non standard utilisée : 'throw (...)'|
|C4988 (niveau 4)|'*symbol*' : variable déclarée en dehors de la portée classe/fonction|
|C5022|'*type*' : plusieurs constructeurs de déplacement spécifiés|
|C5023|'*type*' : plusieurs opérateurs d’assignation de déplacement spécifiés|
|C5024 (niveau 4)|'*type*' : le constructeur de déplacement a été implicitement défini comme étant supprimé|
|C5025 (niveau 4)|'*type*' : l’opérateur d’assignation de déplacement a été implicitement défini comme étant supprimé|
|C5026 (niveau 1 et niveau 4)|'*type*' : le constructeur de déplacement a été implicitement défini comme étant supprimé|
|C5027 (niveau 1 et niveau 4)|'*type*' : l’opérateur d’assignation de déplacement a été implicitement défini comme étant supprimé|
|C5029 (niveau 4)|extension non standard utilisée : les attributs d’alignement en C++ s’appliquent aux variables, aux données membres et aux types de balises uniquement|
|C5031 (niveau 4)|#pragma avertissement (POP) : incompatibilité probable, état d’avertissement envoyé dans un autre fichier <sup>14,1</sup>|
|C5032 (niveau 4)|alerte de #pragma détectée (push) sans avertissement de #pragma correspondant (POP) <sup>14,1</sup>|
|C5034|l’utilisation de «*intrinsic*» intrinsèque entraîne la compilation de la fonction function *-Name* en tant que code invité <sup>15,3</sup>|
|C5035|l’utilisation de la fonctionnalité «*fonctionnalité*» entraîne la compilation de la fonction function *-Name* en tant que code invité <sup>15,3</sup>|
|C5036 (niveau 1)|conversion du pointeur de fonction VarArgs lors de la compilation avec/Hybrid : x86arm64, '*type1*'en'*type2*' <sup>15,3</sup>|
|[C5038](../error-messages/compiler-warnings/c5038.md) (niveau 4)|le membre de données'*membre1*'sera initialisé après le membre de données'*membre2*' <sup>15,3</sup>|
|C5039 (niveau 4)|'*fonction*' : pointeur ou référence à une fonction de déclenchement potentiellement passée à une fonction C extern sous-EHC. Un comportement non défini peut se produire si cette fonction lève une exception. <sup>15,5</sup>|
|C5042 (niveau 3)|'*fonction*' : les déclarations de fonction au niveau de la portée de bloc ne peuvent pas être spécifiées’inline’en C++ standard ; supprimer le spécificateur’inline' <sup>15,5</sup>|
|[C5045](../error-messages/compiler-warnings/c5045.md)|Le compilateur insère l’atténuation spectre pour la charge de mémoire si le commutateur/Qspectre spécifié <sup>15,7</sup>|

<sup>14,1</sup> cet avertissement est disponible à partir de Visual Studio 2015 Update 1. \
<sup>14,3</sup> cet avertissement est disponible à partir de Visual Studio 2015 Update 3. \
<sup>15,3</sup> cet avertissement est disponible à partir de Visual Studio 2017 version 15,3. \
<sup>15,5</sup> cet avertissement est disponible à partir de Visual Studio 2017 version 15,5. \
<sup>15,7</sup> cet avertissement est disponible à partir de Visual Studio 2017 version 15,7. \
<sup>15,8</sup> cet avertissement est disponible à partir de Visual Studio 2017 version 15,8. \
<sup>16,0</sup> cet avertissement est disponible à partir de Visual Studio 2019 RTM. \
<sup>Perm</sup> Autorisation Cet avertissement est désactivé, sauf si l’option du compilateur [/permissive-](../build/reference/permissive-standards-conformance.md) est définie.

## <a name="warnings-off-by-default-in-earlier-versions"></a>Avertissements désactivés par défaut dans les versions antérieures

Ces avertissements ont été désactivés par défaut dans les versions du compilateur antérieures à Visual Studio 2015 :

|Avertissement|Message|
|-|-|
|[C4302](../error-messages/compiler-warnings/compiler-warning-level-2-c4302.md) (niveau 2)|'*conversion*' : troncation de'*type1*'en'*type2*'|
|[C4311](../error-messages/compiler-warnings/compiler-warning-level-1-c4311.md) (niveau 1)|'*variable*' : troncation de pointeur de'*type*'à'*type*'|
|[C4312](../error-messages/compiler-warnings/compiler-warning-level-1-c4312.md) (niveau 1)|'*opération*' : conversion de'*type1*'en'*type2*'d’une taille supérieure|
|[C4319](../error-messages/compiler-warnings/compiler-warning-level-1-c4319.md) (niveau 1)|'*Operator*' : zéro étendant'*type1*'à'*type2*'d’une taille supérieure|

Cet avertissement était désactivé par défaut dans les versions du compilateur antérieures à Visual Studio 2012 :

|Avertissement|Message|
|-|-|
|[C4431](../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md) (niveau 4)|spécificateur de type manquant - int est pris en compte par défaut. Remarque : C ne prend plus en charge int par défaut|

## <a name="see-also"></a>Voir aussi

[warning](../preprocessor/warning.md)
