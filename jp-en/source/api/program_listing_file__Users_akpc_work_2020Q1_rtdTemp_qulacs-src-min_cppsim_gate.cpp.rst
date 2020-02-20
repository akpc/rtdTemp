
.. _program_listing_file__Users_akpc_work_2020Q1_rtdTemp_qulacs-src-min_cppsim_gate.cpp:

Program Listing for File gate.cpp
=================================

|exhale_lsh| :ref:`Return to documentation for file <file__Users_akpc_work_2020Q1_rtdTemp_qulacs-src-min_cppsim_gate.cpp>` (``/Users/akpc/work/2020Q1/rtdTemp/qulacs-src-min/cppsim/gate.cpp``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   bool QuantumGateBase::is_commute(const QuantumGateBase* gate) const{
       for(auto val1 : this->_target_qubit_list){
           for(auto val2 : gate->_target_qubit_list){
               // check gate1 target qubit - gate2 target qubit are commuting
               if ( val1.is_commute_with(val2) == false) return false;
           }
           for(auto val2 : gate->_control_qubit_list){
               // check gate1 target qubit - gate2 control qubit are commuting
               if ( val1.is_commute_with(val2) == false) return false;
           }
       }
       for(auto val1 : this->_control_qubit_list){
           for(auto val2 : gate->_target_qubit_list){
               // check gate1 control qubit - gate2 target qubit are commuting
               if ( val1.is_commute_with(val2) == false) return false;
           }
       }
       // Note: gate1 control - gate2 control are always commuting
       return true;
   }
   
