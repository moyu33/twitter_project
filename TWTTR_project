#pulizia caratteri speciali

punctuation_chars = ["'", '"', ",", ".", "!", ":", ";", '#', '@']
def strip_punctuation(w):
    for c in punctuation_chars:
         w = w.replace(c, "")
    return w 

#accumulo parole positive

positive_words = []
with open("assets/positive_words.txt") as pos_f:
    for lin in pos_f:
        if lin[0] != ';' and lin[0] != '\n':
            positive_words.append(lin.strip())

#accumulo parole negative
            
negative_words = []
with open("assets/negative_words.txt") as pos_f:
    for lin in pos_f:
        if lin[0] != ';' and lin[0] != '\n':
            negative_words.append(lin.strip())
            

#conteggio parole positive            
            
def get_pos(testo_pos):
    counter_pos = 0
    testo_pos = strip_punctuation(testo_pos)
    testo_pos = testo_pos.lower()
    nuovo_testo_pos = testo_pos.split(" ")

    for word in nuovo_testo_pos:
        if word in positive_words:
            counter_pos += 1
    return counter_pos


#conteggio parole negative            

def get_neg(testo_neg):
    counter_neg = 0
    testo_neg = strip_punctuation(testo_neg)
    testo_neg = testo_neg.lower()
    nuovo_testo_neg = testo_neg.split(" ")

    for word in nuovo_testo_neg:
        if word in negative_words:
            counter_neg += 1
    return counter_neg


#creazione e scrittura file.csv con intestazione

twitter_ris = open("resulting_data.csv", "w")
twitter_ris.write("Number of Retweets, Number of Replies, Positive Score, Negative Score, Net Score")
twitter_ris.write('\n')


#connessione ed estrapolazione dat tweet dal file.csv

twitter_primo = open("project_twitter_data.csv", "r")
twitter_primo = twitter_primo.readlines()

top = twitter_primo[0]

div_n = top.strip().split(',') 

#aggiunta dati al file.csv creato

for row in twitter_primo[1:]:
    val = row.strip().split(',')  
    new_s = '{},{},{},{},{}'.format(val[1], val[2], get_pos(val[0]), get_neg(val[0]), get_pos(val[0]) - get_neg(val[0]))
    twitter_ris.write("\n")
