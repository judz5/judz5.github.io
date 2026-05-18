---
layout: project_post
title: Logisim CPU
description: 24-cycle Y86-style processor built in Logisim
year: 2024
tags:
  - Computer Architecture
---

<style>
  .logisim-cpu-hero {
    width: 100%;
    height: auto;
    border: 1px solid #424242;
    border-radius: 0.25rem;
    background: #f8f8f8;
    margin: 0.75rem 0 1.35rem;
  }

  .logisim-cpu-gallery {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 0.85rem;
    margin: 1rem 0 1.5rem;
  }

  .logisim-cpu-gallery figure {
    display: grid;
    grid-template-rows: auto minmax(2.5rem, auto);
    gap: 0.3rem;
    margin: 0;
  }

  .logisim-cpu-image-frame {
    width: 100%;
    aspect-ratio: 4 / 3;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    border: 1px solid #424242;
    border-radius: 0.25rem;
    background: #f8f8f8;
  }

  .logisim-cpu-image-frame img {
    width: 100%;
    height: 100%;
    object-fit: contain;
    display: block;
  }

  .logisim-cpu-gallery figcaption {
    margin: 0;
    color: #aaa;
    font-size: 0.82rem;
    line-height: 1.35;
  }

  .logisim-cpu-pdf-frame {
    width: 100%;
    height: min(58vh, 560px);
    min-height: 340px;
    border: 1px solid #424242;
    border-radius: 0.25rem;
    background: #111;
    margin: 0.75rem 0 1rem;
  }

  @media screen and (max-width: 700px) {
    .logisim-cpu-gallery {
      grid-template-columns: 1fr;
    }

    .logisim-cpu-pdf-frame {
      height: 390px;
      min-height: 320px;
    }
  }
</style>

<img
  class="logisim-cpu-hero"
  src="{{ '/img/projects/logisim-cpu/main.png' | relative_url }}"
  alt="Overview of CPU design">

This project was part of my Computer Organization (CSCE312) class: a CPU built in Logisim with a staged datapath for a Y86-style instruction set. The design breaks each instruction into the same familiar values used in the architecture labs: `icode`, `ifun`, `rA`, `rB`, `valC`, `valP`, `valA`, `valB`, `valE`, and `valM`.

The interesting part was making the whole processor run predictably in hardware logic. Instead of allowing each instruction to take a different path length, the main circuit uses a cycle counter to normalize execution to **24 clock cycles per instruction**:

- cycles `0-9`: fetch the 10-byte instruction from ROM
- cycle `10`: decode and read the register file
- cycle `11`: execute the ALU operation and update condition codes when needed
- cycles `12-20`: read from or write to RAM
- cycle `21`: write results back to the register file
- cycles `22-23`: update the program counter and reset the cycle counter

## Architecture

The processor is split into the usual stages:

- **Fetch** reads a 10-byte instruction from ROM, extracts the instruction fields, and calculates `valP`.
- **Decode** selects `srcA` and `srcB`, reads `valA` and `valB` from the register file, and supports write-back through `dstE`, `dstM`, `valE`, and `valM`.
- **Execute** uses ALU input selectors for `aluA` and `aluB`, decodes `ifun` for arithmetic/logical operations, and sets `ZF`, `SF`, and `OF` condition codes.
- **Memory** controls RAM reads and writes through address/data muxes and enable logic.
- **Write-back** decides whether results should be written from the ALU or memory path.
- **PC update** chooses the next PC from `valP`, `valC`, or `valM`, depending on calls, returns, and conditional control flow.

<div class="logisim-cpu-gallery">
  <figure>
    <div class="logisim-cpu-image-frame">
      <img src="{{ '/img/projects/logisim-cpu/fetch.png' | relative_url }}" alt="Logisim fetch stage circuit">
    </div>
    <figcaption>Fetch stage for instruction bytes, field extraction, and `valP`.</figcaption>
  </figure>
  <figure>
    <div class="logisim-cpu-image-frame">
      <img src="{{ '/img/projects/logisim-cpu/register-file.png' | relative_url }}" alt="Logisim register file and decode circuit">
    </div>
    <figcaption>Register file and decode logic.</figcaption>
  </figure>
  <figure>
    <div class="logisim-cpu-image-frame">
      <img src="{{ '/img/projects/logisim-cpu/alu.png' | relative_url }}" alt="Logisim ALU circuit">
    </div>
    <figcaption>ALU datapath with condition-code logic.</figcaption>
  </figure>
  <figure>
    <div class="logisim-cpu-image-frame">
      <img src="{{ '/img/projects/logisim-cpu/instruction-memory.png' | relative_url }}" alt="Logisim instruction memory circuit">
    </div>
    <figcaption>Instruction memory read/write logic.</figcaption>
  </figure>
  <figure>
    <div class="logisim-cpu-image-frame">
      <img src="{{ '/img/projects/logisim-cpu/pc-update.png' | relative_url }}" alt="Logisim PC update circuit">
    </div>
    <figcaption>PC update logic for sequential flow, calls, jumps, and returns.</figcaption>
  </figure>
</div>

## Takeaway

This project made the abstract CPU diagrams from class feel much more real. Wiring the datapath by hand forced me to think about control signals, mux selection, register timing, memory latency, and how much hidden sequencing is behind a single assembly instruction.
