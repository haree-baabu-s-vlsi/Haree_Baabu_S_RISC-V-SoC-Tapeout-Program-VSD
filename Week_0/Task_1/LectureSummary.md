# Week 0 – Notes on **Digital VLSI SoC Design and Planning** Lecture

## Why Week-0 Matters
This week gave me the big picture of how a design actually travels from an idea in C all the way to working silicon. The main theme I understood is **consistency**. At every stage—C model, RTL, gates, layout, and finally silicon the design must behave the same. If something breaks, I should be able to catch it at that specific stage instead of waiting until the end.


## My Understanding about week 0 lecture:
1. **Start with intent (O1)**  
   I first describe the function in C and verify it with small test cases.  
   This becomes my *baseline truth*.

2. **Describe real hardware (O2)**  
   Next, I write RTL (Verilog). I simulate again and make sure the RTL behaves exactly like the C version.  
   O2 should match O1.

3. **Make gates, not wishes (O3)**  
   Using synthesis, the RTL is turned into a gate-level netlist. I then check logical equivalence so the new netlist still behaves the same.  
   O3 should still match the earlier outputs.

4. **Build a complete SoC**  
   The synthesized blocks are connected with CPU, memories, and peripherals. Integration is where naming, resets, clocks, and address maps need to be handled carefully.

5. **From logic to layout**  
   Physical design takes the netlist into placement, routing, timing closure, and signoff checks like DRC/LVS. The final product here is a GDSII file, which is what the fab uses.

6. **Reality check (O4)**  
   After fabrication, I run the same tests on real silicon. If everything was verified properly, O4 should still match O1, O2, and O3.

---

## The Golden Rule I Took Away
Keep a single source of truth and verify against it at four points:  
- O1 (C model)  
- O2 (RTL)  
- O3 (gate-level netlist)  
- O4 (silicon)  

If any stage does not match, don’t postpone fixing it—debug right there.

---

## One-Liner I’ll Remember
**If O1 == O2 == O3 == O4, the design flow is healthy. If not, the failing checkpoint shows exactly where to look.**
