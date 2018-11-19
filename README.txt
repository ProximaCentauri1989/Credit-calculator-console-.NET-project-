# Credit-calculator-console-.NET-project-

Абстрактный базовый класс Credit задает все необходимые поля и методы, которые используются при расчете кредита 
(наполнении таблицы платежей), в том числе, абструктную функцию Calculate(). Производные классы, как конкретный тип кредита,
накладывают ограничения на такие параметры как максимальный размер денежного заёма и максимальный срок кредитования, 
а так же реализуют функцию расчета кредита (аннуитетный кредит означает погашения ежемесячных задолженностей равными частями,
а дифференциальный по убывающей схеме).

Пример создания обьекта и его использование:

Credit userCredit = new AnnuityCredit(15000, 12, 22,5); //Создать
userCredit.Calculate(); //Расчитать
userCredit.PaymentTable(); //Вывести кредитную таблицу

Credit userCredit2 = (Credit)userCredit.Clone(); //Клонирование кредита (подробная копия)

SortedSet<Credit> creditSet = new SortedSet<Credit> //Расположение кредитов в SortedSet<> (компаратор реализован в классе Credit)
{
    new AnnuityCredit(loan, term, interest),
    new DifferentialCredit(loan, term, interest),
    new AnnuityCreditPlus(loan, term, interest),
    new DifferentialCreditPlus(loan, term, interest)
};

Пример ввода и вывода (аннуитетная схема выплат):

                                   ***CREDIT CALCULATOR***

                    Choose one of the loan types shown below:
                    Annuity [press "1"]
                    Differential [press "2"]
                    Annuity-plus [press "3"]
                    Differential-plus [press "4"]
                    Credit types info [press "5"]

Your option: 1

Input credit conditions:
        Loan: 15000
        Term: 12
        Interest: 22,5

Here is your credit info:
        Loan: 15000 c.u.
        Interest: 22,5%
        Term: 12 monthes
        Taken date: 15.11.2018
        Credit cheme: Annuity
        Maximum possible loan: 100000
        Maximum possible term: 60

CREDIT TABLE:
--------------------------------------------------------------------------------
Period\Month|             Loan|  Whole payment| Credit payment| Percent payment
--------------------------------------------------------------------------------
November               15000,00         1407,53         1126,28          281,25
December               13873,72         1407,53         1147,40          260,13
January                12726,33         1407,53         1168,91          238,62
February               11557,42         1407,53         1190,83          216,70
Marth                  10366,59         1407,53         1213,15          194,37
April                   9153,44         1407,53         1235,90          171,63
May                     7917,54         1407,53         1259,07          148,45
June                    6658,46         1407,53         1282,68          124,85
July                    5375,78         1407,53         1306,73          100,80
August                  4069,05         1407,53         1331,23           76,29
September               2737,82         1407,53         1356,19           51,33
October                 1381,62         1407,53         1381,62           25,91
--------------------------------------------------------------------------------
Loan summary|                 0        16890,33           15000        1890,333
--------------------------------------------------------------------------------


Пример ввода и вывода (дифференциальная схема выплат):

                                   ***CREDIT CALCULATOR***

                    Choose one of the loan types shown below:
                    Annuity [press "1"]
                    Differential [press "2"]
                    Annuity-plus [press "3"]
                    Differential-plus [press "4"]
                    Credit types info [press "5"]

Your option: 2

Input credit conditions:
        Loan: 15000
        Term: 12
        Interest: 22,5

Here is your credit info:
        Loan: 15000 c.u.
        Interest: 22,5%
        Term: 12 monthes
        Taken date: 15.11.2018
        Credit cheme: Differential
        Maximum possible loan: 100000
        Maximum possible term: 60

CREDIT TABLE:
--------------------------------------------------------------------------------
Period\Month|             Loan|  Whole payment| Credit payment| Percent payment
--------------------------------------------------------------------------------
November               15000,00         1531,25         1250,00          281,25
December               13750,00         1507,81         1250,00          257,81
January                12500,00         1484,38         1250,00          234,38
February               11250,00         1460,94         1250,00          210,94
Marth                  10000,00         1437,50         1250,00          187,50
April                   8750,00         1414,06         1250,00          164,06
May                     7500,00         1390,63         1250,00          140,63
June                    6250,00         1367,19         1250,00          117,19
July                    5000,00         1343,75         1250,00           93,75
August                  3750,00         1320,31         1250,00           70,31
September               2500,00         1296,88         1250,00           46,88
October                 1250,00         1273,44         1250,00           23,44
--------------------------------------------------------------------------------
Loan summary|                 0        16828,13           15000        1828,125
--------------------------------------------------------------------------------
