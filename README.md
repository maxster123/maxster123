- 👋 Hi, I’m @maxster123
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
maxster123/maxster123 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
model.setObjective(( 
    
          gp.quicksum(Rückgabeverteilung[NL, NL]    *  Mietverteilung[M] * (PreisGleicheNL[M]   -  Ausleihkosten[M] + 10) * tr[NL, t] for NL, t, M in NiederlassungenTageMietdauer)
        + gp.quicksum(Rückgabeverteilung[NL, NLi]   *  Mietverteilung[M] * (PreisAndereNL[M]    -  Ausleihkosten[M] + 10) * tr[NL, t] for NL, NLi, t, M in TransferTageMietdauer)
        
        + gp.quicksum(Rückgabeverteilung[NL, NL]    *  0.55 *               (30                 -  20               + 10) * tr[NL, 5] for NL in Niederlassungen)
        + gp.quicksum(Rückgabeverteilung[NL, NLi]   *  0.55 *               (50                 -  20               + 10) * tr[NL, 5] for NL, NLi in Transfer)
        
        + gp.quicksum(Rückgabeverteilung[NL, NL]    *  Mietverteilung[M] * (PreisGleicheNL[M]   -  Ausleihkosten[M] + 10) * tr[NL, 5] for NL, M in NiederlassungenMietdauerAmSamstag)
        + gp.quicksum(Rückgabeverteilung[NL, NLi]   *  Mietverteilung[M] * (PreisAndereNL[M]    -  Ausleihkosten[M] + 10) * tr[NL, 5] for NL, NLi, M in TransferMietdauerAmSamstag)
        
        - gp.quicksum(Transferkosten[NL, NLi] * tu[NL, NLi, t] for NL, NLi, t in TransferTage)
        - gp.quicksum(Transferkosten[NL, NLi] * tb[NL, NLi, t] for NL, NLi, t in TransferTage) 
        
        -(KostenRepErwB*ErB + KostenRepErwBzusätzlich*ErBz + KostenRepErwM*ErM + KostenRepErwMzusätzlich*ErMz + KostenRepErwP*ErP)
        
        - 15 * n), 
    
          GRB.MAXIMIZE)
