---
title: Avertissements du compilateur C4800 à C5999
ms.date: 04/21/2019
f1_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4910
- C4916
- C4921
- C4934
- C4951
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5045
- C5046
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5105
- C5106
- C5107
helpviewer_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4910
- C4916
- C4921
- C4934
- C4951
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5045
- C5046
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5105
- C5106
- C5107
ms.openlocfilehash: 518efdd74a90198818538c1548adb2b7ff37290c
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821124"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Avertissements du compilateur C4800 à C5999

Les Articles de cette section de la documentation expliquent un sous-ensemble de messages d’avertissement générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Messages d’avertissement

|Warning|Message|
|-------------|------------|
|[Avertissement du compilateur (niveau 4) C4800](compiler-warning-level-3-c4800.md)| Conversion implicite de'*type*'en bool. Perte d’informations possible |
|[Avertissement du compilateur (niveau 1) C4803](compiler-warning-level-1-c4803.md)|'*méthode*': la méthode Raise a une classe de stockage différente de celle de l’événement, '*Event*'|
|[Avertissement du compilateur (niveau 1) C4804](compiler-warning-level-1-c4804.md)|'*operation*': utilisation risquée du type’bool’dans l’opération|
|[Avertissement du compilateur (niveau 1) C4805](compiler-warning-level-1-c4805.md)|'*operation*': mélange risqué de type'*type1*'et de type'*type2*'dans l’opération|
|[Avertissement du compilateur (niveau 1) C4806](compiler-warning-level-1-c4806.md)|'*opération*': opération risquée: aucune valeur de type'*type1*'promue en type'*type2*'ne peut être égale à la constante donnée|
|[Avertissement du compilateur (niveau 1) C4807](compiler-warning-level-1-c4807.md)|'*operation*': mélange risqué de type'*type1*'et champ de bits signé de type'*type2*'|
|Avertissement du compilateur (niveau 1) C4808|case'*value*'n’est pas une valeur valide pour une condition Switch de type’bool'|
|Avertissement du compilateur (niveau 1) C4809|l’instruction switch a une étiquette’default’redondante; toutes les étiquettes’case’possibles sont fournies|
|[Avertissement du compilateur (niveau 1) C4810](compiler-warning-level-1-c4810.md)|valeur de pragma pack(show) == n|
|[Avertissement du compilateur (niveau 1) C4811](compiler-warning-level-1-c4811.md)|valeur de pragma conform(forScope, show) == value|
|[Avertissement du compilateur (niveau 1) C4812](compiler-warning-level-1-c4812.md)|style de déclaration obsolète: utilisez'*new_syntax*'à la place|
|[Avertissement du compilateur (niveau 1) C4813](compiler-warning-level-1-c4813.md)|'*fonction*': une fonction friend d’une classe locale doit avoir été déclarée précédemment|
|[Avertissement du compilateur (niveau 4) C4816](compiler-warning-level-4-c4816.md)|'*param*': le paramètre a un tableau de taille zéro qui sera tronqué (sauf si l’objet est passé par référence)|
|[Avertissement du compilateur (niveau 1) C4817](compiler-warning-level-1-c4817.md)|'*membre*': utilisation non conforme de'. 'pour accéder à ce membre; compilateur remplacé par'-> '|
|[Avertissement du compilateur (niveau 1) C4819](compiler-warning-level-1-c4819.md)|Le fichier contient un caractère qui ne peut pas être représenté dans la page de codes actuelle (numéro). Enregistrez le fichier au format Unicode pour éviter la perte de données|
|[Avertissement du compilateur (niveau 4) C4820](compiler-warning-level-4-c4820.md)|'*bytes*'octets de remplissage ajoutés après la construction'*Member_Name*'|
|[Avertissement du compilateur (niveau 1) C4821](compiler-warning-level-1-c4821.md)|Impossible de déterminer le type d’encodage Unicode, enregistrez le fichier avec la signature (BOM)|
|[Avertissement du compilateur (niveau 1) C4822](compiler-warning-level-1-c4822.md)|'fonction membre': la fonction membre de classe locale n’a pas de corps|
|[Avertissement du compilateur (niveau 3) C4823](compiler-warning-level-3-c4823.md)|'*fonction*': utilise des pointeurs épingle mais les sémantiques de déroulement ne sont pas activées. Envisagez d’utiliser/EHa|
|Avertissement du compilateur (niveau 2) C4826|La conversion de'*type1*'en'*type2*'est un signe étendu. Cela peut entraîner un comportement inattendu du Runtime.|
|Avertissement du compilateur (niveau 3) C4827|Une méthode’ToString’publique avec 0 paramètre doit être marquée comme Virtual et override|
|[Avertissement du compilateur (niveau 1) C4829](compiler-warning-level-1-c4829.md)|Paramètres potentiellement incorrects de la fonction main. Envisagez’int main (Platform:\<: Array Platform:: String ^ > ^ argv) '|
|[Avertissement du compilateur (niveau 1) C4835](compiler-warning-level-1-c4835.md)|'*variable*': l’initialiseur des données exportées ne sera pas exécuté tant que le code managé n’aura pas été exécuté pour la première fois dans l’assembly hôte|
|Avertissement du compilateur (niveau 4) C4837|trigraphe détecté: '?? *caractère*'remplacé par'*caractère*'|
|[Avertissement du compilateur (niveau 1) C4838](compiler-warning-level-1-c4838.md)|la conversion de'*TYPE_1*'en'*type_2*'requiert une conversion restrictive|
|[Avertissement du compilateur (niveau 3) C4839](compiler-warning-level-3-c4839.md)|utilisation non standard de la classe'*type*'en tant qu’argument d’une fonction variadiques|
|[Avertissement du compilateur (niveau 4) C4840](compiler-warning-level-4-c4840.md)|utilisation non portable de la classe'*type*'en tant qu’argument d’une fonction variadiques|
|Avertissement du compilateur (niveau 4) C4841|extension non standard utilisée: désignateur de membre composé utilisé dans OffsetOf|
|Avertissement du compilateur (niveau 4) C4842|le résultat de’OffsetOf’appliqué à un type utilisant plusieurs héritages n’est pas nécessairement cohérent entre les versions du compilateur|
|Avertissement du compilateur C4843|'*type1*': Un gestionnaire d’exceptions de référence à un type de tableau ou de fonction est inaccessible. Utilisez plutôt'*type2*'|
|Avertissement du compilateur C4844|'Export module *module_name*; 'est désormais la syntaxe préférée pour déclarer une interface de module|
| Avertissement du compilateur (niveau 4) C4845 | '\_\[\|\|declspec (\|no\_init All) 'est ignoré si'/d1initall 0 1 2 3] 'n’a pas été spécifié sur la ligne de commande\_\_ |
| Avertissement du compilateur (niveau 4) C4846 | '*valeur*'n’est pas un argument valide pour'/d1initall': indicateur de ligne de commande ignoré |
| Avertissement du compilateur (niveau 4) C4847 | '\_declspec\_(no\_init\_All) 'ne peut s’appliquer qu’à une fonction, à un type de classe ou à une variable locale: ignoré |
| Avertissement du compilateur (niveau 1) C4848 | la prise en charge de l'\_attribut\_standard «aucune adresse unique» dans c++ 17 et versions antérieures est une extension de fournisseur |
|[Avertissement du compilateur (niveau 4) C4866](c4866.md)| le compilateur ne peut pas appliquer l’ordre d’évaluation de gauche à droite pour l’appel à *operator_name*|
|[Avertissement du compilateur (erreur) C4867](compiler-warning-c4867.md)|'*fonction*': liste d’arguments manquante dans l’appel de fonction; Utilisez'*Call*'pour créer un pointeur vers un membre|
|[Avertissement du compilateur (niveau 4) C4868](compiler-warning-c4868.md)|le compilateur'_file_(*line_number*) 'ne peut pas appliquer l’ordre d’évaluation de gauche à droite dans la liste d’initialisation entre accolades|
|Avertissement du compilateur (niveau 2) C4872|la Division à virgule flottante par zéro a été détectée lors de la compilation du graphique des appels pour l’accès concurrentiel::p arallel_for_each à l’emplacement suivant: '*location*'|
|Avertissement du compilateur (niveau 1) C4880|conversion de’const *TYPE_1*'en'*type_2*': la conversion de cast d’à partir d’un pointeur ou d’une référence peut entraîner un comportement indéfini dans une fonction restreinte amp|
|Avertissement du compilateur (niveau 4) C4881|le constructeur et/ou le destructeur ne sont pas appelés pour la variable tile_static'*variable*'|
|Avertissement du compilateur (niveau 1) C4882|passage d’functors avec des opérateurs d’appel non-const à l’accès concurrentiel::p arallel_for_each est déconseillé|
|[Avertissement du compilateur C4900](compiler-warning-level-1-c4900.md)|Incompatibilité il entre'*Tool1*'version'*version1*'et'*tool2*'version'*version2*'|
|[Avertissement du compilateur (niveau 1) C4905](compiler-warning-level-1-c4905.md)|cast de littéral de chaîne étendu en 'LPSTR'|
|[Avertissement du compilateur (niveau 1) C4906](compiler-warning-level-1-c4906.md)|cast de littéral de chaîne en 'LPWSTR'|
|[Avertissement du compilateur (niveau 1) C4910](compiler-warning-level-1-c4910.md)|'\<identificateur >: ' _ _ declspec (dllexport) 'et’extern’sont incompatibles sur une instanciation explicite|
|[Avertissement du compilateur (niveau 1) C4912](compiler-warning-level-1-c4912.md)|'*attribute*': comportement indéfini de l’attribut sur un UDT imbriqué|
|[Avertissement du compilateur (niveau 4) C4913](compiler-warning-level-4-c4913.md)|l'opérateur binaire défini par l'utilisateur ',' existe mais aucune surcharge n'a pu convertir tous les opérandes, opérateur binaire intégré par défaut ',' utilisé|
|Avertissement du compilateur (niveau 1) C4916|pour avoir un DISPID, '*Description*': doit être introduit par une interface|
|[Avertissement du compilateur (niveau 1) C4917](compiler-warning-level-1-c4917.md)|'*déclarateur*': un GUID ne peut être associé qu’à une classe, une interface ou un espace de noms|
|[Avertissement du compilateur (niveau 4) C4918](compiler-warning-level-4-c4918.md)|'*caractère*': caractère non valide dans la liste d’optimisation pragma|
|[Avertissement du compilateur (niveau 1) C4920](compiler-warning-level-1-c4920.md)|enum enum member member_1 = value_1 déjà rencontré dans enum enum As member_2 = Value_2|
|Avertissement du compilateur (niveau 3) C4921|'*Description*': la valeur d’attribut'*attribut*'ne doit pas être spécifiée par multiplication|
|[Avertissement du compilateur (niveau 1) C4925](compiler-warning-level-1-c4925.md)|'*méthode*': la méthode dispinterface ne peut pas être appelée à partir d’un script|
|[Avertissement du compilateur (niveau 1) C4926](compiler-warning-level-1-c4926.md)|'*identificateur*': symbole déjà défini: attributs ignorés|
|[Avertissement du compilateur (niveau 1) C4927](compiler-warning-level-1-c4927.md)|conversion non conforme; plusieurs conversions définies par l’utilisateur ont été appliquées implicitement|
|[Avertissement du compilateur (niveau 1) C4928](compiler-warning-level-1-c4928.md)|initialisation de copie non conforme ; plusieurs conversions définies par l'utilisateur ont été appliquées implicitement|
|[Avertissement du compilateur (niveau 1) C4929](compiler-warning-level-1-c4929.md)|'*file*': TypeLibrary contient une Union; qualificateur’embedded_idl’ignoré|
|[Avertissement du compilateur (niveau 1) C4930](compiler-warning-level-1-c4930.md)|'*prototype*': fonction prototypée non appelée (une définition de variable est-elle prévue?)|
|[Avertissement du compilateur (niveau 4) C4931](compiler-warning-level-4-c4931.md)|bibliothèque de types présumée construite pour des pointeurs 'nombre' bits|
|[Avertissement du compilateur (niveau 4) C4932](compiler-warning-level-4-c4932.md)|Impossible dedistinguer _ _ identifier \_(identifier) et _Identifier (*identifier*)|
|Avertissement du compilateur (niveau 1) C4934|' _ _ Delegate (multicast) 'est déconseillé, utilisez\_' _ Delegate’à la place|
|[Avertissement du compilateur (niveau 1) C4935](compiler-warning-level-1-c4935.md)|spécificateur d’accès à l’assembly modifié à partir de'*Access*'|
|[Avertissement du compilateur (niveau 1, erreur) C4936](compiler-warning-c4936.md)|ce __declspec est pris en charge uniquement lorsqu'il est compilé avec /clr ou /clr:pure|
|[Avertissement du compilateur (niveau 4) C4937](compiler-warning-level-4-c4937.md)|Impossible de distinguer'*Text1*'et'*text2*'comme arguments de'*directive*'|
|[Avertissement du compilateur (niveau 4) C4938](compiler-warning-level-4-c4938.md)|'*var*': La variable de réduction à virgule flottante peut provoquer des résultats incohérents sous/FP: strict ou #pragma fenv_access|
|[Avertissement du compilateur C4939](compiler-warning-level-1-c4939.md)|#pragma vtordisp est déconseillé et sera supprimé dans une version ultérieure de Visual C++|
|[Avertissement du compilateur (niveau 1) C4944](compiler-warning-level-1-c4944.md)|'*symbol*': impossible d’importer le symbole de'*Assembly1*', car'*symbol*'existe déjà dans la portée actuelle|
|[Avertissement du compilateur (niveau 1) C4945](compiler-warning-level-1-c4945.md)|'*symbol*': impossible d’importer le symbole de'*Assembly1*', car'*symbol*'a déjà été importé à partir d’un autre assembly'*Assembly2*'|
|[Avertissement du compilateur (niveau 1) C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast utilisé entre des classes connexes: '*Class1*'et'*Class2*'|
|[Avertissement du compilateur (niveau 1) C4947](compiler-warning-level-1-c4947.md)|'*type_or_member*': marqué comme obsolète|
|[Avertissement du compilateur (niveau 2) C4948](compiler-warning-level-2-c4948.md)|le type de retour de'*accessor*'ne correspond pas au dernier type de paramètre de la méthode setter correspondante|
|[Avertissement du compilateur (niveau 1 et niveau 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|les pragmas’Managed’et’unmanaged’sont significatifs uniquement lorsqu’ils sont compilés avec'/CLR [: option] '|
|[Avertissement du compilateur (niveau 1, erreur) C4950](compiler-warning-c4950.md)|'*type_or_member*': marqué comme obsolète|
|[Avertissement du compilateur (niveau 1) C4951](compiler-warning-level-1-c4951.md)|'*Function*'a été modifié depuis que les données de profil ont été collectées, données de profil de fonction non utilisées|
|[Avertissement du compilateur (niveau 1) C4952](compiler-warning-level-1-c4952.md)|'*fonction*': aucune donnée de profil trouvée dans la base de données du programme'*pgd_file*'|
|[Avertissement du compilateur (niveau 1) C4953](compiler-warning-level-1-c4953.md)|'*Fonction*'inline a été modifié depuis la collecte des données de profil, données de profil non utilisées|
|Avertissement du compilateur C4954|'*fonction*': non profilé (contient l’expression de switch _ _ Int64)|
|Avertissement du compilateur C4955|'*importation2*': importation ignorée; déjà importé à partir de'*importation1*'|
|[Avertissement du compilateur (niveau 1, erreur) C4956](compiler-warning-c4956.md)|'*type*': ce type n’est pas vérifiable|
|[Avertissement du compilateur (niveau 1, erreur) C4957](compiler-warning-c4957.md)|'*Cast*': le cast explicite de'*cast_from*'en'*cast_to*'n’est pas vérifiable|
|[Avertissement du compilateur (niveau 1, erreur) C4958](compiler-warning-c4958.md)|'*opération*': l’opération arithmétique de pointeur n’est pas vérifiable|
|[Avertissement du compilateur (niveau 1, erreur) C4959](compiler-warning-c4959.md)|Impossible de définir le type non managé'*type*'dans/CLR: safe, car l’accès à ses membres génère du code non vérifiable|
|[Avertissement du compilateur (niveau 4) C4960](compiler-warning-level-4-c4960.md)|'*fonction*'est trop grand pour être profilé|
|[Avertissement du compilateur (niveau 1) C4961](compiler-warning-c4961.md)|Aucune donnée de profil n’a été fusionnée dans 'fichier .pgd', les optimisations guidées par profil sont désactivées|
|[Avertissement du compilateur (niveau 4) C4962](compiler-warning-c4962.md)|'*fonction*': Les optimisations guidées par profil sont désactivées, car les optimisations ont provoqué l’incohérence des données de profil|
|Avertissement du compilateur (niveau 1) C4963|'*Description*': données de profil introuvables; différentes options de compilateur ont été utilisées dans la génération instrumentée|
|[Avertissement du compilateur (niveau 1) C4964](compiler-warning-level-1-c4964.md)|Aucune option d’optimisation n’a été spécifiée; les informations de profil ne seront pas collectées|
|[Avertissement du compilateur (niveau 1) C4965](compiler-warning-level-1-c4965.md)|zone implicite de l’entier 0; utiliser nullptr ou cast explicite|
|Avertissement du compilateur (niveau 1) C4966|'*fonction*'a une annotation __code_seg avec un nom de segment non pris en charge, l’annotation est ignorée|
|Avertissement du compilateur C4970|constructeur délégué: objet cible ignoré, car'*type*'est statique|
|Avertissement du compilateur (niveau 1) C4971|Ordre des arguments \<: objet cible > \<, la fonction cible > pour le constructeur délégué est déconseillée, utilisez \< \<la fonction cible >, target object = "" >|
|[Avertissement du compilateur (niveau 1, erreur) C4972](compiler-warning-c4972.md)|La modification ou le traitement direct du résultat d'une conversion unboxing comme lvalue est non vérifiable|
|Avertissement du compilateur (niveau 1) C4973|'*symbol*': marqué comme déconseillé|
|Avertissement du compilateur (niveau 1) C4974|'*symbol*': marqué comme déconseillé|
|Avertissement du compilateur (niveau 3) C4981|Warbird: fonction'*fonction*'marquée comme _ _ forceinline non inline, car elle contient une sémantique d’exception|
|Avertissement du compilateur (niveau 3) C4985|Symbol Name': attributs absents de la déclaration précédente.|
|[Avertissement du compilateur C4986](compiler-warning-c4986.md)|'*déclaration*': la spécification d’exception ne correspond pas à la déclaration précédente|
|Avertissement du compilateur (niveau 4) C4987|extension non standard utilisée : 'throw (...)'|
|Avertissement du compilateur (niveau 4) C4988|'*variable*': variable déclarée en dehors de la portée classe/fonction|
|Avertissement du compilateur (niveau 4) C4989|'*type*': le type a des définitions en conflit.|
|Avertissement du compilateur (niveau 3) C4990|Warbird: *message*|
|Avertissement du compilateur (niveau 3) C4991|Warbird: fonction'*Function*'marquée comme _ _ forceinline non inline, car le niveau de protection de Inline est supérieur à celui du parent|
|Avertissement du compilateur (niveau 3) C4992|Warbird: fonction'*Function*'marquée comme _ _ forceinline non inline, car elle contient un assembly inline qui ne peut pas être protégé|
|[Avertissement du compilateur (niveau 3) C4995](compiler-warning-level-3-c4995.md)|'*fonction*': le nom a été marqué comme #pragma dépréciée|
|[Avertissement du compilateur (niveau 3) C4996](compiler-warning-level-3-c4996.md)|'*Deprecated-* declaration': *Deprecated-message* (ou "a été déclaré déconseillé")|
|[Avertissement du compilateur (niveau 1) C4997](compiler-warning-level-1-c4997.md)|'*classe*': la coclasse n’implémente pas d’interface com ou de pseudo-interface|
|Avertissement du compilateur (niveau 1) C4998|ÉCHEC de l’attente: *attente*(*valeur*)|
|[Avertissement du compilateur C4999](compiler-warning-level-1-c4999.md)|Avertissement inconnu choisissez la commande support technique du menu aide visuel C++ , ou ouvrez le fichier d’aide du support technique pour plus d’informations|
|Avertissement du compilateur C5022|'*type*': plusieurs constructeurs de déplacement spécifiés|
|Avertissement du compilateur C5023|'*type*': plusieurs opérateurs d’assignation de déplacement spécifiés|
|Avertissement du compilateur (niveau 4) C5024|'*type*': le constructeur de déplacement a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveau 4) C5025|'*type*': l’opérateur d’assignation de déplacement a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveau 1 et niveau 4) C5026|'*type*': le constructeur de déplacement a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveau 1 et niveau 4) C5027|'*type*': l’opérateur d’assignation de déplacement a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveau 1) C5028|'*Name*': L’alignement spécifié dans la déclaration antérieure (*Number*) n’est pas spécifié dans la définition|
|Avertissement du compilateur (niveau 4) C5029|extension non standard utilisée: les attributs d' C++ alignement dans s’appliquent aux variables, aux données membres et aux types de balises uniquement|
|Avertissement du compilateur (niveau 3) C5030|l’attribut'Attribute’n’est pas reconnu|
|Avertissement du compilateur (niveau 4) C5031|#pragma avertissement (POP): incompatibilité probable, état d’avertissement envoyé dans un autre fichier|
|Avertissement du compilateur (niveau 4) C5032|alerte de #pragma détectée (push) sans avertissement de #pragma correspondant (POP)|
|Avertissement du compilateur (niveau 1) C5033|«*Storage-Class*» n’est plus une classe de stockage prise en charge|
|Avertissement du compilateur C5034|l’utilisation de'*intrinsic*'intrinsèque entraîne la compilation de la *fonction* de fonction en tant que code invité|
|Avertissement du compilateur C5035|l’utilisation de la fonctionnalité'*fonctionnalité*'entraîne la compilation de la *fonction* de fonction en tant que code invité|
|Avertissement du compilateur (niveau 1) C5036|conversion du pointeur de fonction VarArgs lors de la compilation avec/Hybrid: x86arm64, '*type1*'en'*type2*'|
|Avertissement du compilateur (erreur) C5037|'*member-function*': une définition hors ligne d’un membre d’un modèle de classe ne peut pas avoir d’arguments par défaut|
|[Avertissement du compilateur (niveau 4) C5038](c5038.md)|le membre de données'*membre1*'sera initialisé après le membre de données'*membre2*'|
|Avertissement du compilateur (niveau 4) C5039|'*fonction*': pointeur ou référence à une fonction de déclenchement potentiellement passée à une fonction C extern sous-EHC. Un comportement non défini peut se produire si cette fonction lève une exception.|
|Avertissement du compilateur (niveau 3) C5040|les spécifications d’exceptions dynamiques sont valides uniquement en C++ 14 et versions antérieures; traitement en tant que noexcept (false)|
|Avertissement du compilateur (niveau 1) C5041|'*définition*': la définition hors ligne du membre de données statique constexpr n’est pas nécessaire et est dépréciée en c++ 17|
|Avertissement du compilateur (niveau 3) C5042|'*déclaration*': les déclarations de fonction au niveau de la portée de bloc ne peuvent pas C++être spécifiées’inline’dans la norme; supprimer le spécificateur’inline'|
|Avertissement du compilateur (niveau 2) avertissements c5043|'*Specification*': la spécification d’exception ne correspond pas à la déclaration précédente|
|Avertissement du compilateur (niveau 4) C5044|Un argument de l’option d’option de ligne de commande pointe vers un chemin d’accès'*path*'qui n’existe pas|
|[Avertissement du compilateur C5045](c5045.md)|Le compilateur insère l’atténuation spectre pour la charge de mémoire si le commutateur/Qspectre est spécifié|
|[Avertissement du compilateur (niveau 2) C5046](c5046.md)|'*fonction*': Symbole impliquant un type avec une liaison interne non définie|
| Avertissement du compilateur (niveau 1) C5047 | utilisation de non standard \_ \_si\_Exists avec modules n’est pas pris en charge |
| Avertissement du compilateur (niveau 1) C5048 | L’utilisation de la macro'*nommacro*'peut entraîner une sortie non déterministe |
| Avertissement du compilateur (niveau 1) C5049 | '*chaîne*': L’incorporation d’un chemin d’accès complet peut entraîner une sortie dépendante de l’ordinateur |
| Avertissement du compilateur (niveau 1) C5050 | Environnement incompatible possible lors de l’importation du module'*module_name*': *problème* |
| Avertissement du compilateur (niveau 1) C5100 | \_\_Les\_arguments\_ vasontréservéspouruneutilisationdans\_ les macros variadiques |
| Avertissement du compilateur (niveau 1) C5101 | l’utilisation de la directive de préprocesseur dans une liste d’arguments de macro de type fonction est un comportement indéfini |
| Avertissement du compilateur (niveau 1) C5102 | définition de macro de ligne de commande non valide'*valeur*'ignorée |
| Avertissement du compilateur (niveau 1) C5103 | le collage de'*TOKEN1*'et'*Token2*'n’entraîne pas la validité d’un jeton de prétraitement |
| Avertissement du compilateur (niveau 1) C5104 | «*Chaîne1*#*Chaîne2*» a été trouvée dans la liste de remplacement de macro, vouliez-vous dire «*Chaîne1*» «#*Chaîne2*»? |
| Avertissement du compilateur (niveau 1) C5105 | l’expansion de macro qui produit’defined’a un comportement indéfini |
| Avertissement du compilateur (niveau 1) C5106 | macro redéfinie avec des noms de paramètres différents |
| Avertissement du compilateur (niveau 1) C5107 | caractère «*char*» de fin manquant |

## <a name="see-also"></a>Voir aussi

[Erreurs etC++ avertissements du compilateur C/du compilateur et des outils de génération](../compiler-errors-1/c-cpp-build-errors.md) \
[Avertissements du compilateur C4000-C5999](compiler-warnings-c4000-c5999.md)
