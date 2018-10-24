---
title: Avertissements du compilateur par version du compilateur | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- devlang-cpp
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- warnings, by compiler version
- cl.exe compiler, setting warning options
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4d815ba1036a03042992d2715e49bbd8f74a28
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990384"
---
# <a name="compiler-warnings-by-compiler-version"></a>Avertissements du compilateur par version du compilateur

Le compilateur peut supprimer les avertissements qui ont été introduites après une version que vous spécifiez à l’aide de la [/WV](../../build/reference/compiler-option-warning-level.md) option du compilateur. Cela est utile pour la gestion de votre processus de génération lorsque vous introduisez une nouvelle version de l’ensemble d’outils et que vous souhaitez supprimer temporairement les avertissements de nouveau. Cette option ne supprime pas les nouveaux messages d’erreur. Nous ne recommandons pas vous supprimer tous les nouveaux avertissements définitivement ! Nous vous recommandons de vous compilez toujours au niveau avertissement régulière la plus élevé, __/W4__et supprimer le __/WV__ option dans votre build dès que possible.

Ces versions du compilateur a introduit de nouveaux avertissements :

| Produit | Numéro de version du compilateur |
|-|-|
| Visual C++ 2002 | 13.00.9466 |
| Visual C++ 2003 | 13.10.3077 |
| Visual C++ 2005 | 14.00.50727.762 |
| Visual C++ 2008 | 15.00.21022.08 |
| Visual C++ 2010 | 16.00.40219.01 |
| Visual C++ 2012 | 17.00.51106.1 |
| Visual C++ 2013 | 18.00.21005.1 |
| Visual C++ 2015 RTM | 19.00.23026.0 |
| Visual C++ 2015 Update 1 | 19.00.23506.0 |
| Visual C++ 2015 Update 2 | 19.00.23918.0 |
| Visual C++ 2015 Update 3 | 19.00.24215.1 |
| Visual C++ 2017 RTM | 19.10.25017.0 |
| Visual C++ 2017 version 15.3 | 19.11.25506.0 |
| Visual C++ 2017 version 15.5 | 19.12.25830.0 |
| Visual C++ 2017 version 15.6 | 19.13.26128.0 |
| Visual C++ 2017 version 15.7 | 19.14.26428.0 |
| Visual C++ 2017 version 15.8 | 19.15.26726.0 |

Vous pouvez spécifier uniquement le numéro principal, les numéros major et minor ou major, minor et les numéros de build pour le __/WV__ option. Le compilateur signale tous les avertissements qui correspondent aux versions qui commencent par le nombre spécifié et supprime tous les avertissements pour les versions supérieures que le nombre spécifié. Par exemple, __/Wv:17__ signale tous les avertissements introduits dans ou avant n’importe quelle version de Visual Studio 2012 et supprime tous les avertissements introduits par n’importe quel compilateur à partir de Visual Studio 2013 (version du 18) ou version ultérieure. Pour supprimer les avertissements introduits dans Visual Studio 2015 update 2 et versions ultérieures, vous pouvez utiliser __/Wv:19.00.23506__. Utilisez __/Wv:19.11__ pour signaler tous les avertissements introduits dans n’importe quelle version de Visual Studio antérieures à Visual Studio 2017 version 15.5, mais supprime les avertissements introduits dans Visual Studio 2017 version 15.5 et versions ultérieure.

Les sections suivantes répertorient les avertissements introduits par chaque version de Visual C++, vous pouvez supprimer à l’aide de la __/WV__ option du compilateur. Le __/WV__ option ne peut pas supprimer les avertissements qui ne sont pas répertoriés, et qui sont antérieurs aux versions spécifiées du compilateur.

## <a name="warnings-introduced-in-visual-c-2017-version-158-compiler-version-1915267260"></a>Avertissements introduits dans Visual C++ 2017 version 15.8 (version du compilateur 19.15.26726.0)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:19.14__.

|||
|-|-|
C5046|«*fonction*' : symbole impliquant le type avec une liaison interne non définie|

## <a name="warnings-introduced-in-visual-c-2017-version-157-compiler-version-1914264280"></a>Avertissements introduits dans Visual C++ 2017 version 15.7 (version du compilateur 19.14.26428.0)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:19.13__.

|||
|-|-|
C4642|«*problème*' : Impossible d’importer les contraintes pour le paramètre générique '*paramètre*»
C5045|Compilateur va insérer l’atténuation de Spectre pour la charge de mémoire si le commutateur/qspectre spécifié

## <a name="warnings-introduced-in-visual-c-2017-version-156-compiler-version-1913261280"></a>Avertissements introduits dans Visual C++ 2017 version 15.6 (version du compilateur 19.13.26128.0)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:19.12__.

|||
|-|-|
C5044|Un argument pour l’option de ligne de commande *option* pointe vers un chemin d’accès '*chemin d’accès*' qui n’existe pas

## <a name="warnings-introduced-in-visual-c-2017-version-155-compiler-version-1912258300"></a>Avertissements introduits dans Visual C++ 2017 version 15.5 (version du compilateur 19.12.25830.0)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:19.11__.

|||
|-|-|
C4843|«*type1*' : un gestionnaire d’exceptions de référence à un type tableau ou fonction est inaccessible, utilisez '*type2*' à la place
C4844|' exporter le module *nom_module*; » est désormais la syntaxe préférée pour déclarer une interface de module
C5039|«*fonction*' : pointeur ou référence à une fonction pouvant lever passé à une fonction C externe sous - EHc. Un comportement non défini peut se produire si cette fonction lève une exception.
C5040|spécifications d’exceptions dynamiques sont valides uniquement dans C ++ 14 et versions antérieures ; traitement en tant que noexcept (false)
C5041|«*définition*' : définition hors ligne pour le membre de données statique constexpr n’est pas nécessaire et est dépréciée en C ++ 17
C5042|«*déclaration*' : les déclarations de fonction à portée de bloc ne peut pas être spécifié 'inline' en C++ standard ; supprimez le spécificateur 'inline'
C5043|«*spécification*' : spécification d’exception ne correspond pas à la déclaration précédente

## <a name="warnings-introduced-in-visual-c-2017-version-153-compiler-version-1911255060"></a>Avertissements introduits dans Visual C++ 2017 version 15.3 (version du compilateur 19.11.25506.0)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:19.10__.

|||
|-|-|
C4597|un comportement indéfini : *description*
C4604|«*type*» : passage d’argument par valeur sur une frontière native / managée nécessite un constructeur de copie valide. Sinon, le comportement d’exécution n’est pas défini
C4749|prise en charge conditionnelle : *description*
C4768|attributs __declspec avant la spécification de liaison sont ignorés.
C4834|Abandon de la valeur de retour de fonction avec l’attribut 'nodiscard'
C4841|extension non standard utilisée : *extension*
C4842|le résultat d '' offsetof' appliqué à un type à l’aide de l’héritage multiple n’est pas garanti pour être cohérente entre les versions du compilateur
C4869|'nodiscard' peut seulement être appliqué aux classes, énumérations et fonctions avec type de retour non void
C5033|«*classe de stockage*' n’est plus une classe de stockage pris en charge
C5034|utiliser des intrinsèques '*intrinsèque*' provoque la fonction *fonction* doit être compilé en tant que code invité
C5035|l’utilisation de fonctionnalité '*fonctionnalité*' provoque la fonction *fonction* doit être compilé en tant que code invité
C5036|conversion de pointeur de fonction varargs durant la compilation avec /hybrid:x86arm64 '*type1*'en'*type2*'
C5037|«*fonction membre*' : une définition hors ligne d’un membre d’un modèle de classe ne peut pas avoir d’arguments par défaut
C5038|membre de données '*member1*'sera initialisé après le membre de données'*member2*'

## <a name="warnings-introduced-in-visual-c-2017-rtm-compiler-version-1910250170"></a>Avertissements introduits dans Visual C++ 2017 RTM (version du compilateur 19.10.25017.0)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:19.00__.

|||
|-|-|
C4468|'fallthrough' : attribut doit être suivi d’une étiquette case ou une étiquette par défaut
C4698|«*fonctionnalité*» est la version d’évaluation uniquement et est susceptible de changer ou mises à jour de la suppression dans les futures.
C4839|utilisation non standard de la classe*classe*» en tant qu’argument à une fonction variadique
C4840|utilisation non portable de la classe*classe*» en tant qu’argument à une fonction variadique

## <a name="warnings-introduced-in-visual-c-2015-update-3-compiler-version-1900242151"></a>Avertissements introduits dans Visual C++ 2015 Update 3 (version du compilateur 19.00.24215.1)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:19.00.23918__.

|||
|-|-|
C4467|l’utilisation d’attributs ATL est déconseillée
C4596|«*nom*' : nom qualifié non conforme dans une déclaration de membre
C4598|' #include \< *en-tête*\>' : numéro de l’en-tête *nombre* dans le *source* ne correspond pas à *source* qui position
C4599|«*argument*' : *source* numéro d’argument *nombre* ne correspond pas à *source*

## <a name="warnings-introduced-in-visual-c-2015-update-2-compiler-version-1900239180"></a>Avertissements introduits dans Visual C++ 2015 Update 2 (version du compilateur 19.00.23918.0)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:19.00.23506__.

|||
|-|-|
C4466|Ne peut pas effectuer d’élision du tas coroutine
C4595|«*classe*' : opérateur non membre new ou delete fonctions ne peuvent pas être déclarées inline
C4828|Le fichier contient un caractère en commençant au décalage 0 x*valeur* qui est non conforme dans le jeu de caractères source actuel (page de codes *nombre*).
C4868|compilateur ne peut pas appliquer l’ordre d’évaluation de gauche à droite dans la liste d’initialiseurs entre accolades

## <a name="warnings-introduced-in-visual-c-2015-update-1-compiler-version-1900235060"></a>Avertissements introduits dans Visual C++ 2015 Update 1 (version du compilateur 19.00.23506.0)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:19.00.23026__.

|||
|-|-|
C4426|indicateurs d’optimisation modifiés après l’en-tête, peut être dû à #pragma optimize()
C4654|Le code placé avant d’inclure d’en-tête précompilé ligne sera ignorée. Ajoutez le code à l’en-tête précompilé.
C5031|#pragma warning (pop) : incompatibilité probable, état d’avertissement envoyé dans un autre fichier
C5032|détecté #pragma warning (push) sans Warning (pop) correspondant #pragma

## <a name="warnings-introduced-in-visual-c-2015-rtm-compiler-version-1900230260"></a>Avertissements introduits dans Visual C++ 2015 RTM (version du compilateur 19.00.23026.0)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/WV : 18__.

|||
|-|-|
C4427|«*erreur*' : dépassement en division constante, un comportement non défini
C4438|«*type*' : ne peut pas être appelée en toute sécurité / await : clrcompat mode. Si '*type*' appels dans le CLR, cela peut entraîner une altération de la tête de CLR
C4455|' opérateur *nom*' : les identificateurs de suffixe littéral qui ne commencent pas par un trait de soulignement sont réservés.
C4456|déclaration de '*nom*' masque la déclaration locale précédente
C4457|déclaration de '*nom*' paramètre de fonction de masque
C4458|déclaration de '*nom*' masque le membre de classe
C4459|déclaration de '*nom*' masque la déclaration globale
C4462|«*type*' : ne peut pas déterminer le GUID du type. Le programme risque d'échouer au moment de l'exécution.
C4463|dépassement de capacité ; affectation *valeur* au champ de bits qui peut contenir uniquement des valeurs à partir de *valeur* à *valeur*
C4473|«*fonction*' : pas assez d’arguments passés pour la chaîne de format
C4474|«*fonction*' : trop d’arguments passés pour la chaîne de format
C4475|'*fonction*' : modificateur de longueur '*modificateur*'ne peut pas être utilisé avec le caractère de champ de type'*caractère*» dans le spécificateur de format
C4476|«*fonction*' : caractère de champ de type inconnu '*caractère*» dans le spécificateur de format
C4477|'*fonction*' : chaîne de format '*chaîne*'requiert un argument de type'*type*', mais l’argument variadique *nombre* a le type '*type*'
C4478|«*fonction*' : Impossible de mélanger des espaces réservés positionnels et non positionnels dans la même chaîne de format
C4494|«*type*' : ignoré __declspec (allocateur) car le type de retour de la fonction n’est pas un pointeur ou une référence
C4495|extension non standard '__super' utilisée : Remplacez par le nom de classe de base explicite
C4496|extension non standard 'for each' utilisée : Remplacez par une instruction ranged-for
C4497|extension non standard 'sealed' utilisée : Remplacez-la par 'final'
C4498|extension non standard utilisée : '*extension*'
C4499|«*spécialisation*' : une spécialisation explicite ne peut pas avoir une classe de stockage (ignorée)
C4576|un type entre parenthèses suivi d’une liste d’initialiseurs est une syntaxe de conversion de type explicite non standard
C4577|'noexcept' utilisé avec le mode spécifié ; aucune des exceptions arrêt sur l’exception n’est pas garanti. Spécifiez /EHsc
C4578|'abs' : conversion de '*type*'en'*type*', perte possible de données (souhaitiez-vous appeler '*nom*' ou à #include \<cmath > ?)
C4582|«*type*' : constructeur n’est pas appelé de manière implicite
C4583|«*type*' : destructeur n’est pas appelé de manière implicite
C4587|«*type*' : changement de comportement : constructeur est appelé n’est plus implicitement
C4588|«*type*' : changement de comportement : destructeur est appelé n’est plus implicitement
C4589|Constructeur de la classe abstraite*type*'ignore l’initialiseur de classe de base virtuelle'*type*'
C4591|limite de profondeur des appels 'constexpr' de *nombre* dépassée (/ constexpr : Depth\<nombre >)
C4592|«*type*' : symbole sera dynamiquement initialisé (limite d’implémentation)
C4593|«*type*' : 'constexpr' appel le limite d’étape d’évaluation de *valeur* dépassée ; utiliser/constexpr : Steps\<numéro > pour augmenter la limite
C4647|changement de comportement : __is_pod (*type*) a une valeur différente dans les versions précédentes
C4648|attribut standard 'carries_dependency' est ignoré
C4649|les attributs sont ignorés dans ce contexte
C4753|Impossible de trouver les limites pour le pointeur ; Fonction intrinsèque MPX sera ignorée
C4771|Limites doivent être créés à l’aide d’un simple pointeur ; Fonction intrinsèque MPX sera ignorée
C4774|«*description*' : chaîne attendue dans l’argument de format *nombre* n’est pas une chaîne littérale
C4775|extension non standard utilisée dans la chaîne de format «*chaîne*'de la fonction'*fonction*'
C4776|' %*caractère*'n’est pas autorisée dans la chaîne de format de la fonction'*fonction*'
C4777|'*description*' : chaîne de format «*chaîne*'requiert un argument de type'*type*», mais l’argument variadique *nombre* a le type '*type*'
C4778|«*description*' : chaîne de format indéterminée '*chaîne*»
C4838|conversion de '*type*'en'*type*' requiert une conversion restrictive
C5022|«*type*' : plusieurs constructeurs de déplacement spécifiés
C5023|«*type*' : plusieurs opérateurs d’assignation de déplacement spécifiés
C5024|«*déclaration*' : constructeur de déplacement a été implicitement défini comme étant supprimé
C5025|«*déclaration*' : déplacement opérateur d’assignation a été implicitement défini comme étant supprimé
C5026|«*type*' : constructeur de déplacement a été implicitement défini comme étant supprimé
C5027|«*type*' : déplacement opérateur d’assignation a été implicitement défini comme étant supprimé
C5028|«*nom*' : alignement spécifié dans la déclaration antérieure (*nombre*) non spécifiée dans la définition
C5029|extension non standard utilisée : les attributs d’alignement en C++ s’appliquent aux variables, les membres de données et les types de balises uniquement
C5030|attribut '*attribut*' n’est pas reconnu

## <a name="warnings-introduced-in-visual-c-2013-compiler-version-1800210051"></a>Avertissements introduits dans Visual C++ 2013 (version du compilateur 18.00.21005.1)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:17__.

|||
|-|-|
C4301|«*type*' : fonction virtuelle de substitution ne diffère de '*déclaration*» par le qualificateur const/volatile
C4316|«*type*' : objet alloué sur le tas ne soit pas aligné *nombre*
C4380|«*type*' : un constructeur par défaut ne peut pas être déconseillé.
C4388|«*jeton*' : incompatibilité signed/unsigned
C4423|'std::bad_alloc' : sera intercepté par la classe ('*type*») sur la ligne *nombre*
C4424|catch pour '*type*'précédé de'*type*' sur la ligne *nombre*; imprévisible peut entraîner si 'std::bad_alloc' est levée.
C4425|Une annotation SAL ne peut pas être appliquée à '...'
C4464|chemin include relatif contient '..'
C4575|'__vectorcall' incompatible avec le « / clr' option : conversion en '__stdcall'
C4609|«*type*'dérive d’interface par défaut'*type*'sur le type'*type*». Utiliser une autre interface par défaut pour '*type*», ou une rupture de la relation de dérivation.
C4754|Les règles de conversion pour les opérations arithmétiques dans la comparaison à *description*(*nombre*) signifient qu’une branche ne peut pas être exécutée. Cast de '*type*'en'*type*» (ou un type similaire de *nombre* octets).
C4755|Les règles de conversion pour les opérations arithmétiques dans la comparaison à *description*(*nombre*) signifient qu’une branche ne peut pas être exécutée dans une fonction inline. Cast de '*type*'en'*type*» (ou un type similaire de *nombre* octets).
C4767|nom de la section «*nom*' est supérieure à 8 caractères et sera tronqué par l’éditeur de liens
C4770|enum partiellement validé '*nom*» utilisé en tant qu’index
C4827|Une méthode 'ToString' publique avec 0 paramètre doit être marqué comme étant virtuel et remplacer
C4882|passage de foncteurs avec opérateurs d’appels non const à concurrency::parallel_for_each est déconseillé
C4973|«*type*' : marqué comme déprécié
C4974|«*type*' : marqué comme déprécié
C4981|Warbird : fonction '*déclaration*' marquée comme __forceinline non inline, car elle contient la sémantique d’exceptions
C4990|Warbird : *message*
C4991|Warbird : fonction '*déclaration*' marquée comme __forceinline non inline, car le niveau de protection de l’inlinee est supérieur au parent
C4992|Warbird : fonction '*déclaration*' marquée comme __forceinline non inline, car elle contient un assembly inline qui ne peut pas être protégé

## <a name="warnings-introduced-in-visual-c-2012-compiler-version-1700511061"></a>Avertissements introduits dans Visual C++ 2012 (version du compilateur 17.00.51106.1)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:16__.

|||
|-|-|
C4330|attribut '*attribut*« pour la section »*section*' ignoré
C4415|en double __declspec (code_seg ('*nom*'))
C4416|__declspec(code_seg(...)) contient une chaîne vide : ignoré
C4417|une instanciation explicite du modèle ne peut pas avoir __declspec(code_seg(...)) : ignoré
C4418|__declspec(code_seg(...)) ignoré sur un enum
C4419|«*nom*'n’a aucun effet lorsqu’il est appliqué à la classe ref privée'*type*».
C4435|«*type*' : la disposition des objets sous/vd2 sera modifiée en raison de la base virtuelle '*type*»
C4436|le dynamic_cast de la base virtuelle '*type*'en'*type*» dans le constructeur ou un destructeur peut échouer avec un objet partiellement construit
C4437|le dynamic_cast de la base virtuelle '*type*'en'*type*' risque d’échouer dans certains contextes
C4443|paramètre pragma attendu doit être '0', '1' ou '2'
C4446|«*type*' : Impossible de mapper le membre '*nom*» dans ce type, en raison de conflits avec le nom de type. La méthode a été renommée en «*nom*'
C4447|signature 'main' trouvée sans modèle de thread. Envisagez d’utiliser ' int main (Platform::Array\<Platform::String ^ > ^ args)'.
C4448|«*type*' n’a pas d’interface par défaut spécifiée dans les métadonnées. Sélection : '*type*», ce qui peut échouer lors de l’exécution.
C4449|«*type*» un type unsealed doit être marqué comme '[WebHostHidden]'
C4450|«*type*'doit être marqué comme '[WebHostHidden]', car il dérive de'*type*»
C4451|«*type*' : l’utilisation de la classe ref*type*' à l’intérieur de ce contexte peut entraîner un marshaling non valide d’objet entre plusieurs contextes
C4452|«*type*' : type public ne peut pas être dans une portée globale. Il doit être dans un espace de noms qui est un enfant du nom du fichier de sortie .winmd.
C4453|«*type*' : un type de '[WebHostHidden]' ne doit pas être utilisé sur la surface publiée d’un type public qui n’est pas '[WebHostHidden]'
C4454|«*type*» est surchargé par plus que le nombre de paramètres d’entrée sans avoir [defaultoverload pour] spécifié. Sélection «*déclaration*» en tant que la surcharge par défaut
C4471|«*nom*' : une déclaration anticipée d’une énumération non délimitée doit avoir un type sous-jacent (int pris par défaut)
C4472|«*nom*' est un enum natif : ajoutez un spécificateur d’accès (publique/privée) pour déclarer un enum géré/WinRT
C4492|«*type*' : méthode de classe ref de base correspond à «*type*», mais n’est ne pas marqué 'override'
C4493|expression de suppression n’a aucun effet car le destructeur de '*type*' n’a pas d’accessibilité 'publique'
C4585|«*type*' : classe unsealed de WinRT A 'public ref class' doit être sealed ou dériver d’un existant
C4586|«*type*' : un type public ne peut pas être déclaré dans un espace de noms de niveau supérieur appelé 'Windows'
C4695|#pragma execution_character_set : '*argument*' n’est pas un argument prises en charge : actuellement, seul « UTF-8' est pris en charge
C4703|variable de pointeur locale potentiellement non initialisée '*nom*' utilisé
C4728|/ Option Yl-ignorée, car une référence PCH est requise
C4745|accès volatile de «*nom*' ne peut pas être honoré en raison de sa taille
C4746|accès volatile de «*nom*' volatile :\<iso\|ms > configuration ; envisagez d’utiliser des fonctions intrinsèques __iso_volatile_load/store
C4872|flottante point de division par zéro détecté lors de la compilation du graphique des appels pour Concurrency::parallel_for_each à l’emplacement : '*description*'
C4880|conversion de '*type*'en'*type*' : cast d’à partir d’un pointeur ou une référence peut entraîner un comportement non défini dans une fonction restreinte à amp
C4881|le constructeur et/ou le destructeur ne sera pas appelé pour la variable tile_static '*type*'
C4966|«*description*' a une annotation __code_seg avec un nom de segment non pris en charge, annotation est ignorée
C4988|«*type*' : variable déclarée en dehors de la portée classe/fonction
C4989|«*description*' : type a des définitions en conflit.

## <a name="warnings-introduced-in-visual-c-2010-compiler-version-16004021901"></a>Avertissements introduits dans Visual C++ 2010 (version du compilateur 16.00.40219.01)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:15__.

|||
|-|-|
C4352|«*nom*' : fonction intrinsèque déjà définie
C4573|l’utilisation de «*type*' exige que le compilateur capture 'this' mais le mode de capture par défaut actuelle ne le permet pas
C4574|«*nom*« est défini comme étant ' 0 » : souhaitiez-vous utiliser ' #if *nom*' ?
C4689|«*caractère*' : caractère non pris en charge dans #pragma detect_mismatch ; #pragma ignoré
C4751|indicateur /arch AVX ne s’applique pas à Intel (r) Extensions Streaming SIMD situés au sein d’inline ASM
C4752|trouvé Intel (r) Advanced Vector Extensions ; envisagez d’utiliser l’indicateur /arch AVX approprié
C4837|trigraphe détecté : ' ?? *caractère*« remplacé par »*caractère*'
C4986|«*déclaration*' : spécification d’exception ne correspond pas à la déclaration précédente
C4987|extension non standard utilisée : 'throw (...)'

## <a name="warnings-introduced-in-visual-c-2008-compiler-version-15002102208"></a>Avertissements introduits dans Visual C++ 2008 (version du compilateur 15.00.21022.08)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:14__.

|||
|-|-|
C4396|«*type*' : le spécificateur inline ne peut pas être utilisé lorsqu’une déclaration friend se réfère à une spécialisation d’un modèle de fonction
C4413|«*déclaration*' : membre de référence est initialisé en temporaire qui ne persiste pas après l’arrêt du constructeur
C4491|«*description*' : a un format de version IDL non conforme
C4603|«*nom*' : macro n’est pas définie ou la définition est différente après utilisation d’un en-tête précompilé
C4627|«*description*' : ignoré lors de la recherche une utilisation d’en-tête précompilé
C4750|«*description*' : fonction with _alloca() inline dans une boucle
C4910|«*type*' : '__declspec (dllexport)' et 'extern' sont incompatibles sur une instanciation explicite
C4985|«*déclaration*' : attributs absents de la déclaration précédente.

## <a name="warnings-introduced-in-visual-c-2005-compiler-version-140050727762"></a>Avertissements introduits dans Visual C++ 2005 (version du compilateur 14.00.50727.762)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:13__.

|||
|-|-|
C4000|Avertissement inconnu, choisissez la commande Support technique dans le menu aide de Visual C++ ou ouvrez le fichier d’aide de Support technique pour plus d’informations
C4272|«*type*' : est marqué comme __declspec (dllimport) ; doit spécifier convention d’appel native lors de l’importation d’une fonction.
C4333|«*expression*' : décalage vers la droite trop important, perte de données
C4334|«*expression*' : résultat du décalage 32 bits converti implicitement en 64 bits (était décalage 64 bits destiné ?)
C4335|Format de fichier Mac détecté : convertissez le fichier source au format DOS ou UNIX
C4342|changement de comportement : '*type*' appelé, mais un opérateur de membre a été appelé dans les versions précédentes
C4350|changement de comportement : '*déclaration*'appelé à la place de'*déclaration*'
C4357|argument de tableau param trouvé dans la liste d’arguments formels pour le délégué '*déclaration*'ignoré lors de la génération'*type*'
C4358|«*expression*' : type de retour des délégués combinés n’est pas 'void' ; la valeur retournée n’est pas définie
C4359|«*type*' : spécificateur d’alignement est inférieur à l’alignement réel (*nombre*) et sera ignoré.
C4362|«*type*' : alignement supérieur à 8 octets n’est pas pris en charge par le CLR
C4364|#using pour l’assembly '*nom*' déjà rencontré à *description*(*nombre*) sans attribut as_friend ; as_friend non appliqué
C4365|«*expression*' : conversion de '*type*'en'*type*', incompatibilité signed/unsigned
C4366|Le résultat de l’unaire «*opérateur*' opérateur peut ne pas être aligné
C4367|Conversion de '*type*'en'*type*' peut entraîner l’exception d’alignement de type de données
C4368|Impossible de définir '*nom*'comme membre de « gérés par*type*' : types mixtes ne sont pas pris en charge.
C4369|«*type*' : valeur de l’énumérateur '*nombre*« ne peut pas être représentée en tant que »*type*«, la valeur est »*nombre*»
C4374|«*déclaration*' : méthode d’interface ne sera pas implémentée par une méthode non virtuelle '*déclaration*»
C4375|méthode non publique '*déclaration*'ne se substitue pas'*déclaration*'
C4376|spécificateur d’accès '*spécificateur*:' n’est plus pris en charge : utilisez '*spécificateur*:' à la place
C4377|les types natifs sont privés par défaut ; -d1PrivateNativeTypes est déconseillé.
C4378|Les pointeurs de fonction pour l’exécution des initialiseurs ; envisagez de System::ModuleHandle::ResolveMethodHandle
C4379|Version *version* du common language runtime ne prend pas en charge ce compilateur. À l’aide de cette version peut provoquer des résultats inattendus
C4381|«*déclaration*' : méthode d’interface ne sera pas implémentée par une méthode non publique '*déclaration*»
C4382|lever '*type*' : un type avec le constructeur de copie ou le destructeur __clrcall ne peut être intercepté que dans/CLR : pure module
C4383|«*type*' : la signification du déréférencement d’un handle peut changer lorsqu’un défini par l’utilisateur '*opérateur*' opérateur existe ; écrivez l’opérateur comme une fonction static pour rendre l’opérande explicite
C4384|#pragma '*directive*' ne doit être utilisée avec une portée globale
C4393|«*type*' : const n’a aucun effet *description* membre de données ; ignoré
C4394|«*type*' : symbole par appdomain ne doit pas être marqué avec __declspec (*valeur*)
C4395|«*type*' : fonction membre sera appelée sur une copie des données membres initonly '*type*»
C4397|DefaultCharSetAttribute est ignoré
C4398|«*type*' : objet global par processus ne peuvent ne pas fonctionne correctement avec plusieurs appdomains ; utilisez __declspec
C4399|«*type*' : symbole par processus ne doit pas être marqué avec __declspec (*valeur*) lors de la compilation avec/clr : pure
C4400|«*type*' : les qualificateurs const/volatile pour ce type ne sont pas pris en charge.
C4412|«*déclaration*' : signature de fonction contient le type '*type*' ; Objets C++ n’est unsafe pour passer entre le code pure et mixte ou natif.
C4429|possible incomplet ou incorrectement formé universel-nom de caractère
C4430|spécificateur de type manquant - int est pris en compte par défaut. Remarque : C++ ne prend pas en charge int par défaut
C4431|spécificateur de type manquant - int est pris en compte par défaut. Remarque : C ne prend plus en charge int par défaut
C4434|un constructeur static doit avoir un accès privé ; modification d’un accès privé
C4439|«*type*' : définition de fonction avec un type managé dans la signature doit avoir une convention d’appel __clrcall
C4441|convention d’appel de '*convention*' ignorée ; «*convention*' utilisé à la place
C4445|«*déclaration*' : dans un type géré/WinRT, une méthode virtuelle ne peut pas être privée
C4460|CLR/WinRT opérateur '*type*», a paramètre passé par référence. CLR/WinRT opérateur '*opérateur*'a une sémantique différente de l’opérateur C++'*opérateur*', voulez-vous effectuer un passage par valeur ?
C4461|«*type*' : cette classe a un finaliseur ' ! *type*» mais pas de destructeur ' ~*type*'
C4470|pragmas de contrôle à virgule flottante ignorés sous /clr
C4480|extension non standard utilisée : spécification du type sous-jacent pour l’enum '*type*'
C4481|extension non standard utilisée : spécificateur de substitution '*spécificateur*'
C4482|extension non standard utilisée : enum '*type*' utilisé dans le nom qualifié
C4483|Erreur de syntaxe : mot clé C++ attendu
C4484|«*type*' : méthode de classe ref de base correspond à «*type*», mais n’est ne pas marqué comme 'virtual', 'new' ou 'override' ; 'new' (et non 'virtual') sont supposé.
C4485|«*type*' : méthode de classe ref de base correspond à «*type*», mais n’est pas marqué comme 'new' ou 'override' ; 'new' (et 'virtual') sont supposés.
C4486|«*type*' : une méthode virtuelle privée d’une classe ref ou d’une classe value doit être marquée comme 'sealed'
C4487|«*type*' : correspond à une méthode non virtuelle héritée '*type*' mais n’est ne pas explicitement marqué comme 'new'
C4488|«*type*' : requiert '*mot clé*'mot_clé pour implémenter la méthode d’interface'*type*»
C4489|'*mot clé*' : non autorisé sur la méthode d’interface '*nom*' ; remplacement spécificateurs sont autorisés uniquement sur les méthodes de classe ref et value
C4490|«*mot clé*' : utilisation incorrecte du spécificateur de substitution ; «*type*' ne correspond pas à une méthode de classe ref de base
C4538|«*type*' : les qualificateurs const/volatile pour ce type ne sont pas pris en charge.
C4559|«*type*' : redéfinition ; la __declspec gains (fonction) (*valeur*)
C4565|«*type*' : redéfinition ; le symbole a été précédemment déclaré avec __declspec (*valeur*)
C4566|caractère représenté par le nom de caractère universel '*caractère*' ne peut pas être représenté dans la page de codes actuelle (*nombre*)
C4568|«*type*' : aucun membre ne correspond à la signature de la substitution explicite
C4569|«*type*' : aucun membre ne correspond à la signature de la substitution explicite
C4570|«*type*' : n’est pas explicitement déclaré comme abstract mais comporte des fonctions abstract
C4571|Information : la sémantique changée depuis Visual C++ 7.1 ; les exceptions structurées (SEH) ne sont plus interceptées
C4572|L’attribut [ParamArray] est déconseillé sous/CLR, utilisez '...' à la place
C4580|[attribute] est déconseillé ; à la place spécifier *spécifié*attribut sous la forme d’une classe de base
C4581|comportement déconseillé : ' «*nom*« ' remplacé par '*nom*' pour traiter l’attribut
C4606|#pragma warning : '*nombre*' ignorée ; Avertissements d’analyse du code ne sont pas associés à des niveaux d’avertissement
C4631|MSXML ou XPath non disponible, les commentaires de document XML ne seront pas traités. *description*
C4632|Commentaire de document XML : *description* -accès refusé : *description*
C4633|Commentaire de document XML*description*: erreur : *description*
C4634|Commentaire de document XML*description*: ne peut pas être appliqué : *description*
C4635|Commentaire de document XML*description*: code XML incorrect : *description*
C4636|Commentaire de document XML*description*: la balise requiert non vide '*description*' attribut.
C4637|Commentaire de document XML*description*: \<inclure > balise ignorée. *description*
C4638|Commentaire de document XML*description*: référence à un symbole inconnu '*description*».
C4639|Erreur MSXML, document XML commentaires ne seront pas traités. *description*
C4641|Commentaire de document XML a une référence croisée ambiguë :
C4678|classe de base*déclaration*'est moins accessible que'*nom*'
C4679|«*description*' : Impossible d’importer le membre
C4687|«*type*' : une classe abstraite sealed ne peut pas implémenter une interface '*type*»
C4688|«*nom*' : liste de contraintes contient un type privé d’assembly '*déclaration*»
C4690|\[ emitidl (pop)] : plus de POP que de push
C4691|«*type*' : type référencé était attendu dans non référencées *module* '*description*', type défini dans l’unité de traduction actuelle utilisée à la place
C4692|«*nom*' : signature de membre non privée contient le type natif privé d’assembly '*déclaration*»
C4693|«*type*' : une classe abstraite sealed ne peut pas avoir de membres d’instance*nom*»
C4694|«*type*' : une classe abstraite sealed ne peut pas avoir une classe de base*type*»
C4720|dans assembleur inline signale : '*description*'
C4721|«*description*' : non disponible comme intrinsèque
C4722|«*description*' : aucun retour du destructeur, fuite de mémoire
C4726|ARM arch4/4 t prend en charge que '\<cpsr_f > ou \<spsr_f >' avec une valeur immédiate
C4727|PCH nommé *nom* avec le même horodatage dans *nom* et *nom*.  À l’aide du premier PCH.
C4729|fonction trop importante pour les avertissements bas‚s sur les graphes de flux
C4730|«*description*» : combinaison de _m64 et expressions peuvent entraîner un code erroné de virgule flottante
C4731|«*description*' : Registre de pointeur frame '*inscrire*' modifié par le code assembleur inline
C4732|intrinsèque '*intrinsèque*' n’est pas pris en charge dans cette architecture
C4733|Affectation de inline asm à 'FS : 0' : gestionnaire non inscrit en tant que gestionnaire safe
C4734|Plus de 64 Ko les numéros de ligne dans un format COFF déboguer la section informations ; arrêt de l’émission de numéros de ligne de débogage COFF pour le module '*module*'
C4738|stockage de résultat flottant 32 bits en mémoire, perte possible de performances
C4739|référence à la variable '*variable*' dépasse son espace de stockage
C4740|flux entrant ou sortant code asm incorporé supprime l’optimisation globale
C4742|«*variable*'a un alignement différent '*emplacement*'et'*emplacement*' : *nombre* et *nombre*
C4743|«*nom*'a une taille différente '*emplacement*'et'*emplacement*' : *nombre* et *nombre* octets
C4744|«*nom*'a un type différent '*emplacement*'et'*emplacement*' : '*type*'et'*type*»
C4747|Appelant managé '*type*' : Impossible d’exécuter du code managé le verrouillage du chargeur, y compris le point d’entrée DLL et les appels accessibles à partir du point d’entrée DLL
C4761|incompatibilité de taille intégrale dans l’argument ; conversion fournie
C4764|Impossible d'aligner les objets de bloc catch sur plus de 16 octets
C4788|«*identificateur*' : identificateur tronqué à '*nombre*' caractères
C4789|mémoire tampon '*nom*» de taille *nombre* octets seront dépassées ; *nombre* octets seront écrits en commençant au décalage *nombre*
C4801|Retour par référence n’est pas vérifiable : *description*
C4819|Le fichier contient un caractère qui ne peut pas être représenté dans la page de codes actuelle (*nombre*). Enregistrez le fichier au format Unicode pour éviter la perte de données
C4826|Conversion de '*type*'en'*type*' type signe étendu. Cela peut provoquer un comportement inattendu de runtime.
C4829|Paramètres potentiellement incorrects de la fonction main. Considérez ' int main (Platform::Array\<Platform::String ^ > ^ argv)'
C4835|«*type*' : l’initialiseur des données exportées ne sera pas exécuté jusqu'à ce que le code managé pour la première fois dans l’assembly hôte
C4867|«*type*' : syntaxe non-standard ; Utilisez '&' pour créer un pointeur vers membre
C4936|ce __declspec est pris en charge uniquement lorsqu'il est compilé avec /clr ou /clr:pure
C4937|«*nom*'et'*nom*« sont impossibles à distinguer en tant qu’arguments pour »*option*»
C4938|«*type*' : variable de réduction de la virgule flottante peut entraîner des résultats incohérents sous/fp : strict ou #pragma fenv_access
C4939|#pragma vtordisp est déconseillé et sera supprimé dans une mise en production ultérieure de Visual C++
C4947|«*type*' : marqué comme obsolète
C4949|les pragmas 'managed' et 'unmanaged' sont significatifs uniquement lors de la compilation avec ' / clr [ : option]'
C4950|«*type*' : marqué comme obsolète
C4955|«*description*' : importation ignorée ; importation déjà effectuée à partir de '*source*»
C4956|«*type*' : ce type n’est pas vérifiable
C4957|«*expression*' : cast explicite de '*type*'en'*type*' n’est pas vérifiable
C4958|«*expression*' : opération arithmétique de pointeur n’est pas vérifiable
C4959|Impossible de définir non managé *classe* '*type*» dans/CLR : safe, car l’accès à ses membres génère du code non vérifiable
C4960|«*description*' est trop grand pour être profilé
C4961|Aucune donnée de profil a été fusionnée dans '*emplacement*», les optimisations guidées par profil désactivées
C4962|«*description*' : les optimisations guidées par profil désactivées, car elles génèrent des incohérences au niveau des données de profil
C4963|«*description*' : aucune donnée de profil trouvée ; les différentes options de compilateur ont été utilisées dans la génération instrumentée
C4964|Aucune option d’optimisation a été spécifiée ; informations de profil ne seront pas collectées.
C4965|boxing implicite de l’entier 0 ; utilisez nullptr ou cast explicite
C4970|constructeur délégué : objet cible ignoré depuis '*déclaration*' est statique
C4971|Ordre des arguments : \<objet cible >, \<fonction cible > pour un constructeur délégué est déconseillé, utilisez \<fonction cible >, \<objet cible >
C4972|La modification ou le traitement direct du résultat d'une conversion unboxing comme lvalue est non vérifiable

## <a name="warnings-introduced-in-visual-c-2003-compiler-version-13103077"></a>Avertissements introduits dans Visual C++ 2003 (version du compilateur 13.10.3077)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:13.00.9466__.

|||
|-|-|
C4343|#pragma optimize (*description*, off) se substitue à l’option /Og
C4344|changement de comportement : utilisation d’arguments template explicites entraîne dans l’appel à '*déclaration*'
C4346|«*type*' : nom dépendant n’est pas un type
C4348|«*déclaration*' : redéfinition du paramètre par défaut : paramètre *nombre*
C4356|«*type*' : données membres static ne peuvent pas être initialisées via une classe dérivée
C4408|anonyme *struct* n’a déclaré aucune donnée membre
C4544|«*déclaration*' : argument template ignoré sur cette déclaration de modèle par défaut
C4545|l’expression avant la virgule correspond à une fonction qui n’a pas de liste d’arguments
C4546|l’appel de fonction avant la virgule n’a pas de liste d’arguments
C4547|«*expression*' : opérateur avant la virgule n’a pas d’effet ; opérateur avec effet secondaire attendu
C4548|l'expression avant la virgule n'a pas d'effet ; expression avec effet secondaire attendu
C4549|«*expression*' : opérateur avant la virgule n’a aucun effet ; souhaitiez-vous utiliser '*expression*' ?
C4628|digrammes non pris en charge avec -Ze. Séquence de caractères '*séquence*'non interprétée comme jeton de remplacement pour'*jeton*'
C4629|digrammes utilisés, séquence de caractères '*séquence*'interprétée comme jeton'*jeton*» (insérer un espace entre les deux caractères si cela n’est pas ce que vous souhaitiez)
C4671|«*description*' : le constructeur de copie est inaccessible
C4676|«*description*' : le destructeur n’est pas accessible
C4677|«*nom*' : signature de membre non privée contient un type privé d’assembly '*déclaration*»
C4686|«*type*' : changement de comportement possible, changement retour UDT convention d’appel
C4812|style de déclaration obsolète : utilisez '*type*::*nom*' à la place
C4813|«*type*' : une fonction friend d’une classe locale doit avoir été précédemment déclarée
C4821|Impossible de déterminer le type d’encodage Unicode, enregistrez le fichier avec la signature (BOM)
C4822|«*type*' : fonction membre de classe locale n’a pas un corps
C4823|«*type*' : utilise des pointeurs épingle mais déroulement sémantique n’est pas activée. Utilisez /EHa
C4913|l'opérateur binaire défini par l'utilisateur ',' existe mais aucune surcharge n'a pu convertir tous les opérandes, opérateur binaire intégré par défaut ',' utilisé
C4948|type de retour de '*déclaration*' ne correspond pas au dernier type de paramètre de la méthode setter correspondante
C4951|«*description*' a été modifié depuis les données de profil, données de profil de fonction non utilisées
C4952|«*description*' : aucune donnée de profil trouvée dans la base de données du programme '*description*»
C4953|Inlinee '*description*' a été modifié depuis le profil de données ont été collectées, les données de profil non utilisées
C4954|«*description*' : non profilé (contient l’expression de switch __int64)

## <a name="warnings-introduced-in-visual-c-2002-compiler-version-13009466"></a>Avertissements introduits dans Visual C++ 2002 (version du compilateur 13.00.9466)

Ces avertissements et tous les avertissements dans les versions ultérieures sont supprimés à l’aide de l’option de compilateur __/Wv:12__.

|||
|-|-|
C4096|«*type*' : interface n’est pas une interface COM ; ne sera pas émise vers IDL
C4097|le paramètre pragma attendu doit être 'restore' ou 'off'
C4165|'HRESULT' est converti en 'bool' ; Êtes-vous sûr que c’est ce que vous voulez ?
C4183|«*nom*' : type de retour manquant supposé pour être une fonction membre retournant 'int'
C4199|*description*
C4255|«*nom*' : aucun prototype de fonction fourni : conversion de '()' en '(void)'
C4256|«*déclaration*' : constructeur de classe avec bases virtuelles a '...' ; appels ne seront ne peut-être pas compatibles avec les versions antérieures de Visual C++
C4258|«*nom*' : définition de la boucle for ignorée ; la définition de la portée englobante est utilisée
C4263|«*déclaration*' : fonction membre ne remplace pas n’importe quelle fonction membre virtuelle de classe de base
C4264|«*déclaration*' : aucune substitution disponible pour la fonction membre virtuelle à partir de la base de '*classe*' ; la fonction est masquée
C4265|«*type*' : classe possède des fonctions virtuelles, mais le destructeur n’est pas virtuel instances de cette classe ne peuvent pas être détruites correctement
C4266|«*déclaration*' : aucune substitution disponible pour la fonction membre virtuelle à partir de la base de '*classe*' ; la fonction est masquée
C4267|«*expression*' : conversion de 'size_t' en '*type*', perte possible de données
C4274|#ident ignoré ; consultez la documentation pour #pragma comment (exestr, 'string')
C4277|élément importé '*type*::*nom*' existe en tant que membre de données et de fonction membre ; donnée membre ignorée
C4278|«*nom*' : identificateur de la bibliothèque de types '*description*' est déjà une macro ; utilisez le qualificateur 'rename'
C4279|«*nom*' : identificateur de la bibliothèque de types '*description*' est un mot clé ; utilisez le qualificateur 'rename'
C4287|«*expression*' : constantes non signées/négatives incompatibles
C4288|extension non standard utilisée : '*nom*' : variable de contrôle de boucle déclarée dans la boucle for est utilisé en dehors de la portée de la boucle ; il est en conflit avec la déclaration de la portée externe
C4289|extension non standard utilisée : '*nom*' : variable de contrôle de boucle déclarée dans la boucle for est utilisée en dehors de la portée de la boucle
C4293|«*expression*' : shift nombre négatif ou trop important, comportement non défini
C4295|«*type*' : tableau est trop petit pour comporter un caractère null de fin
C4296|«*expression*' : expression est toujours *valeur*
C4297|«*type*' : fonction supposé ne pas pour lever une exception, mais pas
C4298|«*nom*' : identificateur dans la bibliothèque de types '*description*' est déjà une macro ; renommer en ' __*nom*»
C4299|'*nom*' : identificateur de la bibliothèque de types '*description*» est un mot clé ; le changement de nom à ' __*nom*'
C4302|«*expression*' : troncation de '*type*'en'*type*»
C4303|*conversion* à partir de '*type*'en'*type*» est déconseillé, utilisez static_cast, __try_cast ou dynamic_cast
C4314|paramètre pragma attendu doit être '32' ou '64'
C4315|«*type*' : pointeur 'this' pour le membre '*type*' ne peut pas être alignée *nombre* comme prévu par le constructeur
C4318|en passant de constante zéro comme longueur de memset
C4319|«*expression*' : zéro étendant '*type*'en'*type*' d’une taille supérieure
C4321|génération automatique d’un IID pour l’interface '*type*'
C4322|génération automatique d’un CLSID pour la classe*type*'
C4323|réutilisez le CLSID inscrit pour la classe*type*'
C4324|«*type*' : structure a été remplie en raison du spécificateur d’alignement
C4325|attributs pour la section «*description*' ignoré
C4326|type de retour de '*nom*'doit être'*type*« au lieu de »*type*'
C4327|«*expression*' : alignement d’indirection de LHS (*nombre*) est supérieur à celui de RHS (*nombre*)
C4328|«*description*' : alignement d’indirection du paramètre formel *nombre* (*nombre*) est supérieure à l’alignement de l’argument réel (*nombre*)
C4329|spécificateur d’alignement ignoré sur enum
C4336|Importer la bibliothèque de types à références croisées '*bibliothèque*'avant d’importer'*description*'
C4337|bibliothèque de types à références croisées '*bibliothèque*'in'*description*» est automatiquement importé
C4338|#pragma *description*: section standard '*section*» est utilisé
C4339|«*type*' : utilisation du type non défini détectée dans les métadonnées CLR/WinRT - utilisation de ce type peut provoquer une exception runtime
C4353|extension non standard utilisée : constante 0 comme expression de fonction.  Utilisez la fonction intrinsèque '__noop' à la place
C4370|«*déclaration*' : la disposition de classe a changé depuis une version précédente du compilateur en raison d’une meilleure compression
C4371|«*déclaration*' : la disposition de classe a peut-être changé d’une version précédente du compilateur en raison d’une meilleure compression du membre '*membre*»
C4373|«*type*' : substitutions de fonctions virtuelles*déclaration*», les versions précédentes du compilateur n’ont pas été substituées lorsque les paramètres ne différaient que par les qualificateurs const/volatile
C4387|«*description*' : a été considéré comme
C4389|«*expression*' : incompatibilité signed/unsigned
C4391|«*déclaration*' : type de retour incorrect pour la fonction intrinsèque, attendue '*type*»
C4392|«*déclaration*' : nombre incorrect d’arguments de fonction intrinsèque, attendu '*nombre*' arguments
C4407|cast entre différentes représentations du pointeur en membre, le compilateur peut générer du code incorrect
C4420|'*nom*' : opérateur non disponible, à l’aide de «*nom*' à la place ; le contrôle à l’exécution peut être compromis
C4440|redéfinition de convention d’appel '*description*'en'*description*' ignoré
C4442|terminateur null incorporée dans un argument __annotation.  Valeur sera tronquée.
C4444|«*nom*' : '__unaligned' de niveau supérieur n’est pas implémenté dans ce contexte
C4526|«*type*' : fonction membre statique ne peut pas substituer la fonction virtuelle '*déclaration*' substitution ignorée, fonction virtual sera masquée
C4531|Gestion des exceptions C++ non disponible sous Windows CE. Utiliser la gestion structurée des exceptions
C4532|'*description*' : saut hors *enfin* bloc a un comportement indéfini lors de la gestion de l’arrêt
C4533|l’initialisation de '*déclaration*' est ignorée par ' goto *déclaration*'
C4534|«*déclaration*' ne sera pas un constructeur par défaut pour *classe* '*type*' en raison de l’argument par défaut
C4535|appel de _set_se_translator() requiert /EHa
C4536|«*description*' : nom de type dépasse la limite métadonnées de '*nombre*' caractères
C4537|«*déclaration*' : '.' appliqué à un type non UDT
C4542|Génération ignorée du fichier texte injecté fusionné, Impossible d’écrire *type* fichier : '*filename*' : *erreur*
C4543|Injecté supprimé par l’attribut de texte « aucune\_injected_text'
C4555|l'expression n'a pas d'effet ; attendue expression avec effets secondaires
C4557|'__assume' contient l’effet '*effet*»
C4558|valeur de l’opérande '*nombre*'est hors limites'*nombre* - *nombre*'
C4561|'__fastcall' incompatible avec le « / clr' option : conversion en '__stdcall'
C4562|fonctions entièrement prototypées sont requises avec la « / clr' option : conversion de '()' en '(void)'
C4564|méthode '*nom*» de *classe* '*type*« définit le paramètre par défaut non pris en charge »*paramètre*'
C4584|«*type*' : classe de base*déclaration*'est déjà une classe de base de'*déclaration*»
C4608|Initialisation de plusieurs membres d’union : '*type*'et'*type*'
C4619|#pragma warning : numéro d’avertissement inexistant '*nombre*'
C4623|«*type*' : constructeur par défaut a été implicitement défini comme étant supprimé
C4624|«*type*' : destructeur a été implicitement défini comme étant supprimé
C4625|«*type*' : constructeur de copie a été implicitement défini comme étant supprimé
C4626|«*type*' : opérateur d’assignation a été implicitement défini comme étant supprimé
C4645|fonction déclarée avec 'noreturn' a une instruction return
C4646|la fonction déclarée avec 'noreturn' a le type de retour non void
C4659|#pragma '*description*' : utilisation du segment réservé '*nom*' a un comportement indéfini, utilisez #pragma comment (linker,...)
C4667|«*déclaration*' : aucun modèle de fonction défini correspondant à l’instanciation n’imposée
C4668|«*nom*'n’est pas défini comme préprocesseur ou macro, remplacement par '0' pour'*valeur*»
C4669|«*expression*' : conversion risquée : '*type*' est un objet de type de gérés/WinRT
C4674|«*nom*' doit être déclaré 'static' et avoir un seul paramètre
C4680|«*type*' : coclasse ne spécifie pas une interface par défaut
C4681|«*type*' : coclasse ne spécifie pas une interface par défaut qui est une source d’événement
C4682|«*type*' : aucun attribut de paramètre directionnel spécifié, [in] pris par défaut
C4683|«*déclaration*' : source de l’événement a un 'out'-paramètre ; faites attention lorsque vous raccordez plusieurs gestionnaires d’événements
C4684|«*description*' : avertissement !! attribut peut entraîner une génération de code non valide : utilisez avec précaution
C4685|'> >' attendu, '>>' trouvé lors de l'analyse des paramètres du modèle
C4700|variable locale non initialisée '*nom*' utilisé
C4701|variable locale potentiellement non initialisée '*nom*' utilisé
C4702|code inaccessible
C4711|fonction '*nom*' sélectionnée pour expansion inline automatique
C4714|fonction '*déclaration*' marquée comme __forceinline non inline
C4715|«*fonction*' : pas de tous les chemins de contrôle retournent une valeur
C4716|«*fonction*' : doit retourner une valeur
C4717|«*fonction*' : récurrent sur tous les chemins d’accès de contrôle, la fonction entraînera un débordement de pile d’exécution
C4718|«*fonction*' : appel récurrent n’a pas d’effets secondaires, suppression
C4719|Constante double trouvée avec Qfast spécifié - utilisez 'f' comme suffixe pour indiquer simple précision
C4723|division potentielle par 0
C4724|modulo potentiel par 0
C4725|l'instruction peut manquer de précision sur certains processeurs Pentium
C4757|indice est une valeur non signée élevée, souhaitiez-vous une constante négative ?
C4772|#import a référencé un type à partir d’une bibliothèque de types manquante ; «*description*' utilisé comme espace réservé
C4792|fonction '*fonction*' déclarée à l’aide de sysimport et référencée à partir du code natif ; bibliothèque d’importation requise pour lier
C4794|segment de variable de stockage local de thread '*nom*« a été remplacée par »*segment*'en'*segment*'
C4798|code natif généré pour la fonction p-code '*nom*» avec le Gestionnaire d’exceptions ou les sémantiques de déroulement
C4799|fonction '*nom*' a aucune instruction EMMS
C4803|«*déclaration*' : la méthode raise a une classe de stockage différent de celui de l’événement, '*déclaration*»
C4810|valeur de pragma Pack (Show) == *nombre*
C4811|valeur de pragma conform (forScope, show) == *valeur*
C4820|«*type*' : '*nombre*' octets de remplissage ajoutés après *type* '*type*»
C4905|littéral de chaîne étendu converti en «*type*'
C4906|effectuer un cast de littéral de chaîne «*type*'
C4912|«*attribut*' : attribut comportement indéfini sur un UDT imbriqué
C4916|pour avoir un dispid, '*type*' : doit être introduites par une interface
C4917|«*type*' : un GUID ne peut être associé à une classe, d’interface ou espace de noms
C4918|«*caractère*' : caractère non valide dans la liste d’optimisation pragma
C4920|enum *nom* membre *nom*=*nombre* déjà rencontré dans enum *nom* comme *nom* = *nombre*
C4921|«*nom*' : valeur de l’attribut '*valeur*' ne doit pas être spécifiée plusieurs fois
C4925|«*déclaration*' : la méthode dispinterface ne peut pas être appelée à partir du script
C4926|«*déclaration*' : symbole déjà défini : attributs ignorés
C4927|conversion non conforme ; plusieurs conversions définies par l’utilisateur ont été appliquées implicitement
C4928|initialisation de copie non conforme ; plusieurs conversions définies par l'utilisateur ont été appliquées implicitement
C4929|«*description*' : typelibrary contient une union ; en ignorant le qualificateur 'embedded_idl ' ignoré
C4930|«*déclaration*' : fonction prototypée non appelée (était une définition de variable souhaitée ?)
C4931|Nous présumons que la bibliothèque de types a été générée pour *nombre*-bit des pointeurs
C4932|__identifier (*description*) et __identifier (*description*) ne se distinguent pas
C4934|'__delegate (Multicast)' est déconseillé, utilisez '__delegate' à la place
C4935|spécificateur d’accès l’assembly modifié à partir de '*description*'
C4944|«*nom*' : ne peut pas importer le symbole de '*source*' : en tant que*déclaration*' existe déjà dans la portée actuelle
C4945|«*nom*' : ne peut pas importer le symbole de '*source*' : en tant que*déclaration*'a déjà été importé à partir d’un autre assembly'*source*»
C4946|reinterpret_cast utilisé entre des classes connexes : '*déclaration*'et'*déclaration*'
C4995|«*nom*' : nom a été marqué comme #pragma deprecated
C4996|«*problème*' : *description*
C4997|«*type*' : coclasse n’implémente pas une interface COM ou pseudo-interface
C4998|Échec de l’attente : *description*(*nombre*)

## <a name="see-also"></a>Voir aussi

- [Option de compilateur/WV](../../build/reference/compiler-option-warning-level.md)
- [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md)
- [warning](../../preprocessor/warning.md)
